<template>
  <slot-in-child-render></slot-in-child-render>
  <slot-in-render :message="'Test message'" #default="props">
    {{ props.text }} - {{ props.title }}
  </slot-in-render>
</template>

<script>
import SlotInChildRender from "./components/SlotInChildRender.vue";
import SlotInRender from "./components/SlotInRender.vue";

export default {
  name: "App",
  components: {
    SlotInChildRender,
    SlotInRender,
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
