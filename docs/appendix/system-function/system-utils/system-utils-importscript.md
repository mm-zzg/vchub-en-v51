# System.Utils.importScript


## Description

Import a JavaScript file.

## Grammar

**System.Utils.importScript(scriptFileUrl: string): Promise`<void>`**

- Parameter 

    scriptFileUrl - Script file path  

- Return 

    Nothing

## Code Example

Create a table using vue+element-ui.

```typescript 

await System.Utils.importStyle('https://unpkg.com/element-ui/lib/theme-chalk/index.css');
await System.Utils.importScript('https://unpkg.com/vue@2/dist/vue.js');
await System.Utils.importScript('https://unpkg.com/element-ui/lib/index.js');
// Execute before Vue initialization
document.body.innerHTML = `<div id='app'>
    <el-table
      :data="tableData"
      style="width: 500px">
      <el-table-column
        prop="date"
        label="date"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="name"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="address">
      </el-table-column>
    </el-table>
</div>`;
// @ts-ignore
new Vue({
    el: '#app',
    data: function () {
        return {
            tableData: [{
                date: '2016-05-02',
                name: 'WAGO VC Hub',
                address: 'Jinshajiang Road, Putuo District, Shanghai'
            }, {
                date: '2016-05-04',
                name: 'WAGO VC Hub',
                address: 'Jinshajiang Road, Putuo District, Shanghai '
            }, {
                date: '2016-05-01',
                name: 'WAGO VC Hub',
                address: 'Jinshajiang Road, Putuo District, Shanghai '
            }, {
                date: '2016-05-03',
                name: 'WAGO VC Hub',
                address: 'Jinshajiang Road, Putuo District, Shanghai'
            }]
        }
    }
});

```  
