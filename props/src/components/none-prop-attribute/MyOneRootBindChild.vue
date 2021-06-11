<template>
  <div>
    <div class="date-picker" v-bind="$attrs"> <!-- This v-bind  cooperate with inheritAttrs options -->
      <input type="datetime-local" />
    </div>
  </div>
</template>

<script>
export default {
  name: "MyOneRootBindChild",
  inheritAttrs: false, //Not inherit attrs to root element
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
