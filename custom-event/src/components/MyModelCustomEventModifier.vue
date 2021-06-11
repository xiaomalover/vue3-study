<template>
  <div>
    <input
      type="text"
      :value="modelValue"
      @input="emitValue"
    />
  </div>
</template>

<script>
export default {
  name: "MyModelCustomEventModifier",

  props: {
    modelValue: String,
    modelModifiers: {
      default: () => ({})
    }
  },

  created() {
    console.log(this.modelModifiers) // {trim: true, my_capitalize: true }
  },

  methods: {
    emitValue(e) {
      let value = e.target.value
      if (this.modelModifiers.my_capitalize) {
        value = value.charAt(0).toUpperCase() + value.slice(1)
      }
      this.$emit('update:modelValue', value)
    }
  },

  emits: ["update:modelValue"],
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
