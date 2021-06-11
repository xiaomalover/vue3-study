<template>
  <div class="hello">
    <p>Number prop: {{numberProp}}</p>
    <p>Multiple prop: {{multipleProp}}</p>
    <p>Required string prop: {{requiredStringProp}}</p>
    <p>Number with default prop: {{numberWithDefaultProp}}</p>
    <p>String with default prop: {{stringWithDefaultProp}}</p>
    <p>Object with default prop: {{objectWithDefaultProp}}</p>
    <p>Custom validator prop: {{customValidatorProp}}</p>
    <p>Function with default prop: {{functionWithDefaultProp}}</p>

  </div>
</template>

<script>
export default {
  
  name: "MyPropsValidate",

  props: {

    //Default and required options can be used with type options 

    // Basic type check (`null` and `undefined` values will pass any type validation)
    numberProp: Number,

    // Multiple possible types
    multipleProp: [String, Number],

    // Required string
    requiredStringProp: {
      type: String,
      required: true
    },

    // Number with a default value
    numberWithDefaultProp: {
      type: Number,
      default: 100
    },

    // String with a default value
    stringWithDefaultProp: {
      type: String,
      default: "Hello world"
    },

    // Object with a default value
    objectWithDefaultProp: {
      type: Object,
      // Object or array defaults must be returned from
      // a factory function
      default() {
        return { message: 'hello' }
      }
    },

    // Custom validator function
    customValidatorProp: {
      //default: "success",
      validator(value) {
        // The value must match one of these strings
        return ['success', 'warning', 'danger'].includes(value)
      }
    },

    // Function with a default value
    functionWithDefaultProp: {
      type: Function,
      // Unlike object or array default, this is not a factory function - this is a function to serve as a default value
      default() {
        return 'Default function'
      }
    }
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
