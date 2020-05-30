# FindThatLoot-ref
Library of resources, ideas for my endavours, creating FindThatLoot to have all in one place remotely available.

### 1. Fuzzy matching
```
Fuzzy matching has one big side effect; it messes up with relevance. Although Damerau-Levenshtein is an algorithm that considers most of the common user’s misspellings, it also can include a significantly the number of false positives, especially when we are using a language with an average of just 5 letters per word, such as English. That is why most of the search engine frameworks prefer to stick with Levenshtein distance. 
```
- [Example](https://blog.couchbase.com/fuzzy-matching/)

#### Levnshtein distance 
1. https://rosettacode.org/wiki/Levenshtein_distance 
```
Also known as Edit Distance, it is the number of transformations 
(deletions, insertions, or substitutions) required to transform a source string into the target one.
For example, if the target term is “book” and the source is “back”, 
you will need to change the first “o” to  “a” and the second “o” to “c”, 
which will give us a Levenshtein Distance of 2.
```
1. [ES2015+ Implementation](https://rosettacode.org/wiki/Levenshtein_distance#ES6)

#### Damerau-Levenshtein distance 
```
It is an extension to Levenshtein Distance, allowing one extra operation: Transposition of two adjacent characters:
Ex: TSAR to STAR
Damerau-Levenshtein distance = 1  (Switching S and T positions cost only one operation)
Levenshtein distance = 2  (Replace S by T and T by S)
```
### 2. Libs
1. https://fusejs.io/ - seems realy easy, no dependencies
1. https://bevacqua.github.io/horsey/ - horsey (oglądałem wcześniej) dużo możliwości jak
  - lazy ajax loading (remote files)
  - limiting list results
  - custom output rendering ```renderItem: function(li, suggestion) {...```
  

### Functionality Enabling
1. https://bevacqua.github.io/dragula/ - drag & drop (throwin out of container!!!)
1. https://bevacqua.github.io/insignia/ - customizable tags input creation - managing choosed mods visualy ( removable with x as i wanted earlier)
### 3. Regex Trie
https://github.com/aggixx/PoBPreviewBot/commit/71201cfab4c650f18cd22e73adef6c24d58b116f - aggix bot implementation for single item check
https://www.scitepress.org/Papers/2016/60066/60066.pdf
### can use
- https://www.heroicons.com
- tps://tailwindcss.com
- https://www.reddit.com/r/pathofexile/comments/7dpd8y/qol_fuzzy_search_for_name_and_mods_on_poeappcom/ - fuzzy searching
- https://github.com/Traf27/node-poe-api - poe api for public stash data, but nice template for private ones
  - https://www.npmjs.com/package/request-promise

### some planed features
same as in main repository
- support for 1 recently used Character or Selected Character, N stash tabs from Standard
- Better stash tabs caching, and updating, with ability to manualy delate items
- Searching through all Uniques and their mods, as separate page to league view (probably fuzzy search)
- Support for gem xp, and incubator as bar 
- Support for upcoming leagues
- Nice ui
- item links to pathofexile.com/trade/ with preselected mods
  - or with mods of user choice
 

