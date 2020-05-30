
### How to create data for mods 
1. copy source code from https://poedb.tw/us/mod.php?l=1
1. copy html in tag <div id="Modsmod_item_list" aria-expanded="true" class="collapse in" style="">

#### cleaning data:
1. replace  <td role="row""> with {
1. replace </td> with }
1. replace first <td>xx</td> with "ilvl": xx,   <---comma here is important
1. replace secound <td>XXfix</td> with "affixType": "xxfix",
1. get rid of <del>xxxx</del> strings
1. add field "tags":[], 
1. replace ....


Data structure I would want to convert it to (work in progress)
```json
{
  "ilvl": 68,
  "affixType": "Prefix",
  "tag": [],
  "name": "# to # Cold Damage if you've dealt a Critical Strike Recently",
  "range": [
    {
      "min": 16,
      "max": 20
    },
    {
      "min": 20,
      "max": 25
    }
  ]
}

```
