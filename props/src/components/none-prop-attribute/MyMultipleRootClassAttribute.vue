<template>
    <header>Header not bind class</header>
    <main v-bind="$attrs">Main bind class because use v-bind="$attrs"</main>
    <footer>Footer not bind class</footer>
</template>

<script>
export default {
  name: "MyMultipleRootClassAttribute",
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
