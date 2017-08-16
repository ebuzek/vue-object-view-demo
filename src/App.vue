<template>
  <div id="app">
    <VueObjectView v-model="string" />
    <VueObjectView v-model="boolean" />
    <VueObjectView v-model="number" />
    <VueObjectView v-model="_undefined" />
    <VueObjectView v-model="nullVal" />
    <VueObjectView v-model="object1" />
    <VueObjectView v-model="object2" />
    <VueObjectView v-model="array1" />
    <VueObjectView v-model="array2" />
    <VueObjectView v-model="array3" />
    <VueObjectView v-model="array4" />
    
  </div>
</template>

<script>
import VueObjectView from 'vue-object-view';

let string = "This is a string";
let boolean = true;
let _null = null;
let _undefined = undefined;
let number = 3.14;

let object1 = {
  string,
  boolean,
  "null": null,
  "undefined" : undefined,
  number
}


let object2 = {
  string,
  boolean
}
object2.self = object2;

let array1 = [
  string,
  boolean,
  null,
  undefined,
  number
]

let array2 = [...Array(256).keys()];

let array3 = [ string, boolean ];
let object3 = { array: array3 };
array3[3] = object3;


let array4 = [ object1, object2 ]

export default {
  name: 'app',
  data () {
    return {
      string,
      boolean,
      _undefined: undefined,
      nullVal: null,
      number,
      object1,
      object2,
      array1,
      array2,
      array3,
      array4
    }
  },
  components: {
    VueObjectView
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
