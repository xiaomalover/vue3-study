<template>
  <div>
    <input
      type="text"
      :value="testModifiers1"
      @input="emitValue"
    />
  </div>
</template>

<script>
export default {
  name: "MyModelAttributeCustomEventModifier",

  props: {
    testModifiers1: String,
    testModifiers1Modifiers: {//v-model:attribute use name attributeModifiers
      default: () => ({})
    }
  },

  created() {
    console.log(this.testModifiers1Modifiers) // {trim: true, my_capitalize: true }
  },

  methods: {
    emitValue(e) {
      let value = e.target.value
      if (this.testModifiers1Modifiers.my_capitalize) {
        value = value.charAt(0).toUpperCase() + value.slice(1)
      }
      this.$emit('update:testModifiers1', value)
    }
  },

  emits: ["update:testModifiers1"],
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
