## Acquiring Mods data

### PoeDBB has subpages with mod for various different items 
As author said if you replace **mod.php?** with **json.php/Mods/Gen?** you will get json object back

For example:
https://poedb.tw/us/json.php/Mods/Gen?cn=Sacrifice_of_the_Vaal

Here are all item links from https://poedb.tw/us/mod.php?l=1 html code
(sadly I have not found way to get (is it possible?) all item data json links)

<pre>
https://poedb.tw/us/json.php/Mods/Gen

Influency:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Sacrifice_of_the_Vaal">Vaal</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Elder">The Elder</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shaper">The Shaper</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Crusader">The Crusader</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Redeemer">The Redeemer</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Hunter">The Hunter</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Warlord">The Warlord</a>

Weapons
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Claw">Claws</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Dagger">Daggers</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Wand">Wands</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=One Hand Sword">One Hand Swords</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Thrusting One Hand Sword">Thrusting One Hand Swords</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=One Hand Axe">One Hand Axes</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=One Hand Mace">One Hand Maces</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Sceptre">Sceptres</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Rune Dagger">Rune Daggers</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Bow">Bows</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Staff">Staves</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Two Hand Sword">Two Hand Swords</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Two Hand Axe">Two Hand Axes</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Two Hand Mace">Two Hand Maces</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=FishingRod">Fishing Rods</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Warstaff">Warstaves</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Convoking+Wand">Convoking Wand</a>

Jewels
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Crimson+Jewel">Crimson Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Viridian+Jewel">Viridian Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Cobalt+Jewel">Cobalt Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Prismatic+Jewel">Prismatic Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Murderous+Eye+Jewel">Murderous Eye Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Searching+Eye+Jewel">Searching Eye Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Hypnotic+Eye+Jewel">Hypnotic Eye Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Ghastly+Eye+Jewel">Ghastly Eye Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Timeless+Jewel">Timeless Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Large+Cluster+Jewel">Large Cluster Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Medium+Cluster+Jewel">Medium Cluster Jewel</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=BaseItemTypes&an=Small+Cluster+Jewel">Small Cluster Jewel</a>

Jewellery
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Amulet">Amulets</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Ring">Rings</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Ring&an=unset_ring">Unset Ring</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Belt">Belts</a>

Armour:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=str_armour">Gloves(Str)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=dex_armour">Gloves(Dex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=int_armour">Gloves(Int)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=str_dex_armour">Gloves(StrDex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=str_int_armour">Gloves(StrInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Gloves&an=dex_int_armour">Gloves(DexInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=str_armour">Boots(Str)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=dex_armour">Boots(Dex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=int_armour">Boots(Int)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=str_dex_armour">Boots(StrDex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=str_int_armour">Boots(StrInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Boots&an=dex_int_armour">Boots(DexInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=str_armour">Body Armours(Str)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=dex_armour">Body Armours(Dex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=int_armour">Body Armours(Int)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=str_dex_armour">Body Armours(StrDex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=str_int_armour">Body Armours(StrInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=dex_int_armour">Body Armours(DexInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Body+Armour&an=str_dex_int_armour">Body Armours(StrDexInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=str_armour">Helmets(Str)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=dex_armour">Helmets(Dex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=int_armour">Helmets(Int)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=str_dex_armour">Helmets(StrDex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=str_int_armour">Helmets(StrInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Helmet&an=dex_int_armour">Helmets(DexInt)</a>

Off-Hands
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Quiver">Quivers</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=str_armour,str_shield">Shields(Str)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=dex_armour,dex_shield">Shields(Dex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=int_armour,focus">Shields(Int)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=str_dex_armour,str_dex_shield">Shields(StrDex)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=str_int_armour,str_int_shield">Shields(StrInt)</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Shield&an=dex_int_armour,dex_int_shield">Shields(DexInt)</a>

Flasks:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=LifeFlask">Life Flasks</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=ManaFlask">Mana Flasks</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=HybridFlask">Hybrid Flasks</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=UtilityFlask">Utility Flasks</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=UtilityFlaskCritical">Critical Utility Flasks</a>

From previous leagues:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Delve">Delve</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Bestiary">Bestiary</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Incursion">Incursion</a>

Labirynth Enchants Need to Get Manualy:
<a href="/us/mod.php?type=enchantment&an=helmet">helmet</a>
<a href="/us/mod.php?type=enchantment&an=boots">boots</a>
<a href="/us/mod.php?type=enchantment&an=gloves">gloves</a>

(Not-needed)Maps:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Map&an=low_tier_map">low_tier_map</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Map&an=mid_tier_map">mid_tier_map</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Map&an=top_tier_map">top_tier_map</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Map&an=old_map">old_map</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Map&an=secret_area">secret_area</a>

(Not-needed)Strongboxes:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Strongbox">Strongbox</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Cartographer%27s+Strongbox">Cartographer's Strongbox</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Gemcutter%27s+Strongbox">Gemcutter's Strongbox</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Chemist%27s+Strongbox">Chemist's Strongbox</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Arcanist%27s+Strongbox">Arcanist's Strongbox</a>
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=Chest&an=Jeweller%27s+Strongbox">Jeweller's Strongbox</a>

(Not-needed)Sextants Manualy:
<a href="/us/mod.php?type=Sextant">Sextant</a>

(Not-needed)Monsters:
<a href="https://poedb.tw/us/json.php/Mods/Gen?cn=monster">Monster</a>
(Not-needed)Manualy:
<a href="/us/mod.php?type=monster&an=MonsterNemesis">MonsterNemesis</a>
<a href="/us/mod.php?type=monster&an=Bloodlines">Bloodlines</a>
<a href="/us/mod.php?type=monster&an=Torment">Torment</a>
</pre>
