<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <my-props
      static-string="This is static string value"
      :dynamic-string="post.title"
      :dynamic-and-static-string="post.title + ':' + post.id"
      :static-number="24"
      :dynamic-number="post.id"
      :static-boolean="true"
      :dynamic-boolean="post.isNew"
      imply-boolean
      :static-array="[10, 20, 30]"
      :dynamic-array="post.keywords"
      :staticObject="{name: 'Zhang san', age: 33}"
      :dynamicObject="post.author"
      v-bind="allObject"
    />

  </div>
</template>

<script>
import MyProps from "./components/MyProps.vue";

export default {
  name: "App",
  data() {
    return {
      post: {
        title: "This is dynamic string value",
        id: 1,
        isNew: false,
        keywords: ["hot", "new", "recommend"],
        author: {name: 'Li si', age: 44}
      },
      allObject: {
        allObjectAttr1: "string",
        allObjectAttr2: 1,
        allObjectAttr3: false,
      }
    };
  },
  components: {
    MyProps,
  },
};
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
