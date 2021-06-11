<template>
  <div>
    <input
      type="text"
      :value="firstName"
      @input="$emit('update:firstName', $event.target.value)"
    />
    -
    <input
      type="text"
      :value="lastName"
      @input="$emit('update:lastName', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  name: "MyModelMultipleAttributeCustomEvent",

  props: {
    firstName: String,
    lastName: String,
  },

  emits: ["update:firstName", "update:lastName"],
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
