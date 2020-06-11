import json
import sqlite3
import os
from typing import Any, List, Callable

REPOE_DATA_DIRECTORY = 'D:/dev/github/RePoE-master/data/'
#DB_PATH = './db/.sqlite'
DB_PATH = './db/.mods.db'


def delete_file(file_path: str) -> None:
    if os.path.exists(file_path):
        os.remove(file_path)


def read_json_from_file(file_path: str) -> Any:
    with open(file_path, 'r') as json_file:
        return json.load(json_file)


def import_to_db(json_path: str, connection: sqlite3.Connection, import_function: Callable[[List, sqlite3.Cursor], None]) -> None:
    data_type = os.path.basename(
        json_path)[:os.path.basename(json_path).find('.')]
    print('\tImporting {0} from {1}...'.format(data_type, json_path))
    cursor = connection.cursor()

    print('\t\tLoading JSON to memory... ', end='')
    json_data = read_json_from_file(json_path)
    print('Done!')

    print('\t\tImporting into database... ', end='')
    import_function(json_data, cursor)
    print('Done!')

    connection.commit()
    print('\t{0} imported!'.format(data_type.capitalize()))


def create_db_schema(database: sqlite3.Connection) -> None:
    print('Creating database schema... ', end='')
    cursor = database.cursor()

    # Primary data tables (no refs)
    cursor.execute('''
                    CREATE TABLE tags(
                       id INTEGER PRIMARY KEY AUTOINCREMENT,
                       name TEXT NOT NULL
                   )''')

    cursor.execute('''
                    CREATE TABLE effects(
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        name TEXT NOT NULL,
                        display_name TEXT
                   )''')

    cursor.execute('''
                    CREATE TABLE stats(
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        name TEXT NOT NULL,
                        is_aliased INTEGER NOT NULL,
                        is_local INTEGER NOT NULL
                    )''')

    cursor.execute('''
                    CREATE TABLE mods(
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        name TEXT NOT NULL,
                        domain TEXT NOT NULL,
                        generation_type TEXT NOT NULL,
                        mod_group TEXT NOT NULL,
                        essence_only INT NOT NULL,
                        ingame_name TEXT,
                        required_level INT NOT NULL
                    )''')

    # Secondary data tables (with refs)
    cursor.execute('''
                    CREATE TABLE stat_aliases(
                        stat_id INTEGER NOT NULL,
                        alias_id INTEGER NOT NULL,
                        PRIMARY KEY (stat_id, alias_id),
                        FOREIGN KEY (stat_id)
                            REFERENCES stats(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (alias_id)
                            REFERENCES stats(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE                  
                    )''')

    cursor.execute('''
                    CREATE TABLE stat_translations(
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        stat_id INTEGER NOT NULL,
                        condition_min INTEGER,
                        condition_max INTEGER,
                        translation TEXT NOT NULL,
                        FOREIGN KEY (stat_id)
                            REFERENCES stats(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''
                    CREATE TABLE mod_stats(
                        mod_id INTEGER NOT NULL,
                        stat_id INTEGER NOT NULL,
                        min_value INTEGER NOT NULL,
                        max_value INTEGER NOT NULL,
                        PRIMARY KEY (mod_id, stat_id),
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (stat_id)
                            REFERENCES stats(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''
                    CREATE TABLE mod_effects(
                        mod_id INTEGER NOT NULL,
                        effect_id INTEGER NOT NULL,
                        level INTEGER NOT NULL,
                        PRIMARY KEY(mod_id, effect_id),
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (effect_id)
                            REFERENCES effects(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''
                    CREATE TABLE mod_buffs(
                        id INTEGER PRIMARY KEY AUTOINCREMENT,
                        mod_id INTEGER NOT NULL,
                        buff TEXT NOT NULL,
                        range INTEGER NOT NULL,
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''
                    CREATE TABLE mod_spawn_weights(
                        mod_id INTEGER NOT NULL,
                        tag_id INTEGER NOT NULL,
                        weight INTEGER NOT NULL,
                        PRIMARY KEY(mod_id, tag_id),
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (tag_id)
                            REFERENCES tags(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''  
                    CREATE TABLE mod_generation_weights(
                        mod_id INTEGER NOT NULL,
                        tag_id INTEGER NOT NULL,
                        weight INTEGER NOT NULL,
                        PRIMARY KEY(mod_id, tag_id),
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (tag_id)
                            REFERENCES tags(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    cursor.execute('''
                    CREATE TABLE mod_tags(
                        mod_id INTEGER NOT NULL,
                        tag_id INTEGER NOT NULL,
                        PRIMARY KEY(mod_id, tag_id),
                        FOREIGN KEY (mod_id)
                            REFERENCES mods(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE,
                        FOREIGN KEY (tag_id)
                            REFERENCES tags(id)
                            ON DELETE CASCADE
                            ON UPDATE CASCADE
                    )''')

    database.commit()
    print('Done!')


def import_tags(tags: List, cursor: sqlite3.Cursor) -> None:
    # Tags are simply an array, so we push it directly
    data = [(tag,) for tag in tags]
    cursor.executemany('INSERT INTO tags(name) VALUES (?)', data)


def import_effects(gems: dict, cursor: sqlite3.Cursor) -> None:
    # I'm gonna treat gems as effects, since gems JSON contains all the mod effects, not only gems info
    # Gems JSON has a lot of data, we want only the name and displayed name.
    # name is the primary object name
    # display_name is the in-game human readable name (name: active_skill: display_name)
    data = [(gem, gems[gem].get('active_skill', {'display_name': gem}).get(
        'display_name', gem)) for gem in gems]
    cursor.executemany(
        'INSERT INTO effects(name, display_name) VALUES (?,?)', data)


def import_stats(stats: dict, cursor: sqlite3.Cursor) -> None:
    # stats is a flat dict-list so it should be easy
    data = [(stat, stats[stat].get('is_aliased', False),
             stats[stat].get('is_local', False)) for stat in stats]
    cursor.executemany(
        'INSERT INTO stats(name, is_aliased, is_local) VALUES (?,?,?)', data)


def import_stat_aliases(stats: dict, cursor: sqlite3.Cursor) -> None:
    for (stat, stat_data) in stats.items():
        if stat_data['is_aliased']:
            cursor.execute('SELECT id FROM stats WHERE name=?', (stat,))
            stat_id = cursor.fetchone()[0]
            for (stat_alias_type, stat_alias_name) in stat_data['alias'].items():
                cursor.execute(
                    'SELECT id FROM stats WHERE name=?', (stat_alias_name,))
                alias_id = cursor.fetchone()[0]
                cursor.execute(
                    'INSERT INTO stat_aliases(stat_id, alias_id) VALUES (?,?)', (stat_id, alias_id))


def import_stat_translations(translations: dict, cursor: sqlite3.Cursor) -> None:
    pass


def import_mods(mods: dict, cursor: sqlite3.Cursor):
    for mod in mods:
        pass


def import_data(repoe_data_path: str, connection: sqlite3.Connection) -> None:
    print('Importing data...')

    data_import_table = [
        ('tags.min.json', import_tags),
        ('gems.min.json', import_effects),
        ('stats.min.json', import_stats),
        ('stats.min.json', import_stat_aliases),
        ('stat_translations.min.json', import_stat_translations),
        ('mods.min.json', import_mods)
    ]

    for (file, import_func) in data_import_table:
        import_to_db(os.path.join(repoe_data_path, file),
                     connection, import_func)


def main() -> None:
    delete_file(DB_PATH)
    print('Opening database {0}'.format(DB_PATH))
    database_connection = sqlite3.connect(DB_PATH)
    database_cursor = database_connection.cursor()
    database_cursor.execute('PRAGMA foreign_keys = ON')
    database_connection.commit()

    create_db_schema(database_connection)

    import_data(REPOE_DATA_DIRECTORY, database_connection)

    database_connection.commit()
    database_connection.close()


if __name__ == '__main__':
    main()
