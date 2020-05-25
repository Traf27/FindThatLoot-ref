# FindThatLoot-ref
Library of resources, ideas for my endavours, creating FindThatLoot to have all in one place remotely available.

### Fuzzy matching and relevance

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
#### Libs
1. https://fusejs.io/ - seems realy easy, no dependencies


