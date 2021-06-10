<template>
  <div class="hello">
    <p>Static string prop: {{ staticString }}</p>
    <p>Dynamic string prop: {{ dynamicString }}</p>
    <p>Dynamic and static string prop: {{ dynamicAndStaticString }}</p>

    <p>Static number prop: {{ staticNumber }}</p>
    <p>Dynamic number prop: {{ dynamicNumber }}</p>

    <p>Static boolean prop: {{ staticBoolean }}</p>
    <p>Dynamic boolean prop: {{ dynamicBoolean }}</p>
    <p>Imply boolean: {{ implyBoolean }}</p>

    <p>
      <span v-for="(item, index) in staticArray" :key="index">
        {{ index }} - {{ item }} &nbsp;&nbsp;&nbsp;&nbsp;
      </span>
    </p>
    <p>
      <span v-for="(item, index) in dynamicArray" :key="index">
        {{ index }} - {{ item }} &nbsp;&nbsp;&nbsp;&nbsp;
      </span>
    </p>

    <p>Static object prop: {{ staticObject }}</p>
    <p>Dynamic object prop: {{ dynamicObject }}</p>

    <p>All object to assign item: {{allObjectAttr1}} - {{allObjectAttr2}} - {{allObjectAttr3}} </p>

    <!-- The prop attribute stream should only from parent to child, child can not update them. -->
    <button @click="incStaticNumberProp">Good experience: Whrite prop attribute related【none-reference: not array、object】 (static number: {{staticNumber}}; static number's mirror: {{staticNumberMirror}}) </button>
    <br/><br/>
    <button @click="updateStatiObjectProp">Bad experience: Whrite prop attribute related 【reference: array、object】 (static object: {{staticObject}}; static object's mirror: {{staticObjectMirror}}) </button>
    <p>Read a property related to prop via computed attribute： {{ageText}}</p>
    
  </div>
</template>

<script>
export default {
  
  name: "MyProps",

  data() {
    return {
      // We can't update the prop attribute, so we copy it's value to local data attribute, so we can update local data attribute.
      staticNumberMirror: this.staticNumber,
      
      // Note that objects and arrays in JavaScript are passed by reference, 
      //so if the prop is an array or object, mutating the object or array itself inside the child component will affect parent state.
      staticObjectMirror: this.staticObject
    }
  },

  methods: {
    
    incStaticNumberProp() {
      /* //This is the bad experience, will throw error in compier time.
      this.staticNumber++ */
      
      //This is the good experience, because we update the local data.
      this.staticNumberMirror++
    },
    updateStatiObjectProp() {
      this.staticObjectMirror.age++;
    }
  },

  computed: {
    ageText() {
      return "My age is: " + this.staticNumber
    }
  },

  /**
   * If the props defined as array,
   * the props will not validate type
   */
  //props: ['msg', 'title']

  /**
   * If the props defined as json,
   * the props will validate type.
   */
  props: {
    //String
    staticString: String,
    dynamicString: String,
    dynamicAndStaticString: String,
    //Number
    staticNumber: Number,
    dynamicNumber: Number,
    //Boolean
    staticBoolean: Boolean,
    dynamicBoolean: Boolean,
    implyBoolean: Boolean,
    //Array
    staticArray: Array,
    dynamicArray: Array,
    //Object
    staticObject: Object,
    dynamicObject: Object,

    //All object assign item
    allObjectAttr1: String,
    allObjectAttr2: Number,
    allObjectAttr3: Boolean
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
