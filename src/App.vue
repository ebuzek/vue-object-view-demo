<template>
  <div id="app">
    <div class="header">
    <h2>Vue Object View</h2>
    <p>A light-weight component for displaying arbitrary JavaScript objects.</p>
    </div>
    <h4>Why?</h4>
    <p>This component is useful for displaying JavaScript values of all types. It can handle primitive values (i.e., Boolean, Null, Numbers...), but it's especially useful for viewing larger structured values like <strong>nested objects and arrays</strong>. The coolest thing is that it handles correctly <strong>circular references</strong>, in other words, you can display objects that contain themselves (JSON.stringify() would fail for such values...).</p>
    <p>Vue-object-view was created to build the in-browser <strong>JavaScript debugger</strong> in the <a href="http://emanuelbuzek.eu/parapple/">Parapple</a> project.</p>
    <p>The following examples should show how the component displays various JavaScript values.</p>
    <h4>Primitive types</h4>
    <VueObjectView v-model="string" />
    <VueObjectView v-model="boolean" />
    <VueObjectView v-model="number" />
    <VueObjectView v-model="_undefined" />
    <VueObjectView v-model="nullVal" />
    <h4>Objects</h4>
    <p>
      An ordinary JS object containing various types...
      <VueObjectView v-model="object1" />
    </p>
    
    <p>
      The following object is <strong>cirular</strong> - it contains a reference to itself.
      <VueObjectView v-model="object2" />
    </p>
    
    <h4>Arrays</h4>
    <p>
      An array containing mixed types...
      <VueObjectView v-model="array1" />
    </p>
    <p>
      A slightly longer array with 256 elements...
      <VueObjectView v-model="array2" />
    </p>
    <p>
      An array containing an object that contains the array itself - another <strong>circular structure</strong>
      <VueObjectView v-model="array3" />
    </p>
    <p>
      Another array with infite objects... 
      <VueObjectView v-model="array4" />
    </p>
    
    <h4>Additional properties</h4>
    <p>
      Setting <strong>nowrap = false</strong> allows the inline mode to wrap across multiple lines:
      <VueObjectView v-model="array2" :nowrap="false" />
    </p>

    <p>
      The expand button text can be changed using <strong>expandButtonText</strong> property:
      <VueObjectView v-model="object2" expandButtonText="expand" />
    </p>

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
  color: #2c3e50;
  margin-top: 60px;
}
div.header {
  text-align: center;
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
