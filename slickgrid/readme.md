## FindThatLoot datatable essentials

https://github.com/6pac/SlickGrid/wiki/Grid-Introduction

### Useful slickgrid opions
- "syncColumnCellResize": true  (resizes colum while holding mouse, instead of only after release of button
- "enableColumnReorder": true

#### maybe will be used
1. "selectedCellCssClass": "selected"  (feature to select row, although i could use onClick event on row in jquery)
1. "multiSelect": true (selcting more then few items at a time for: delete, move to favourites, move to category: like build:"Zombiemancer Baron", move to stash tab->would need to downloa stash again)
1. "fullWidthRows": true (expand grid to the max width of its container)
1. cellFlashingCssClass if we would turn focus of user to indicate something...hm

#### Adnotations
2) There should be log feature, so user could found out all his actions made so far, would be able to make the same ingame, could be also yes/no dialog to accept/reject delete/move action, with ability to turn it off in functions.


#### check later
- "enableAddRow"
- "defaultFormatter"
- "dataItemColumnValueExtractor"
- "asyncPostRenderDelay"
- "asyncEditorLoadDelay"
- "asyncEditorLoading":	false	Makes cell editors load asynchronously after a small delay. This greatly increases keyboard navigation speed.
