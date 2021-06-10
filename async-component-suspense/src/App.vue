<template>
  <img alt="Vue logo" src="./assets/logo.png">
  
  <!-- Suspense demo component start -->
  <my-suspense/>
  <!-- Suspense demo component end -->

</template>

<script>
import MySuspense from './components/MySuspense.vue'

export default {
  name: 'App',
  components: {
    MySuspense
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
