# vue-confirm-select

Vue select component

#### Installation

```
npm i -D vue-confirm-select
```


#### Example

```
<confirm-select :title="Title"
                :list="selectList"
                :edit="'[e]'" :ok="'OK'" :cancel="'Cancel'"
                :callback="selection => myMethod(selection)"/>
```

```
import ConfirmSelect from 'vue-confirm-select'
```

```
components: {
    ConfirmSelect
}

data: function () {
  return {
    selectionList: [
      { title: 'None', value: null },
      { title: 'Option1', value: '1' }
      { title: 'Option2', value: '2' }
      { title: 'Option3', value: '3' }
    ]
  }
},

methods: {
  myMethod: function (selection) {
    console.log(`Selected ${selection}`)
  }
}
```
