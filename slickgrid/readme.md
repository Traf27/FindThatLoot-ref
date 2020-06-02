## FindThatLoot datatable essentials

#### How-to
- [Introduction](https://github.com/6pac/SlickGrid/wiki/Grid-Introduction)
- [Subscribing to **Events**, and list of them](https://github.com/6pac/SlickGrid/wiki/Grid-Events)

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

#### Notes about usin with React.js

```
@DemGiran i used it in my React project. Actually, i do not recommend to use SlickGrid in React.JS if you don't have to use it. You can check react-table for as a pure react component.
SlickGrid has many issues and problems when you want to use it in React.JS
However, if you gonna do that just simply add slickgrid as npm package in your project. And import the all necessary files (jquery, slickgrid core js files and plugins) in your main js file.
Then create a react class and render SlickGrid then use it everywhere like;

<SlickGrid
columns={this.state.columns}
data={this.state.data}
gridOptions={{ forceFitColumns: true }}
/>
```
