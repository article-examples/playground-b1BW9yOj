To Render the Model Data
{{propsName}}
<div v-html="propsName"></div>

Iterating the Array of Items in Model
<li v-for="(item, index) in items">
  {{item.text}} <button v-on:click="deleteItem(index)">X</button>
</li>

Adding Click event
<input type="text"   v-on:keypress.enter="addItem" id="fruit" />
<input type="button" v-on:click="addItem">

Adding Filters
<div>{{propsName | greet}}</div>

Adding Dynamic / Computed Props
<div>Total: {{totalItems}}</div>

Adding Watches
<input v-model="input">

Simple Vue.JS
var card = new Vue({
  el: '#card',
  data: {
    propsName: 'propsvalue',
    items: [
      { text: 'Apple' },
      { text: 'Orange' },
      { text: 'Graphes' },
    ],
    totalItems: 0,
  },
  methods: {
    addItem: function () {
      var newFruit = document.getElementById('fruit').value;

      if(newFruit !== '') {
        this.items.push({
          text: newFruit,
        });
      }
    },
    deleteItem: function (index) {
      this.items.splice(index, 1);
    }
  },
  filters: {
    greet: function (name) {
      return "Hi " + name;
    }
  },
  computed: {
    totalItems: function () {
      return this.items.length;
    }
  },
  watch: {
    input: function () {
      this.propsName = 'changed';
    }
  }
  })
