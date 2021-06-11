<template>
  <h1>This is the demo for custom event</h1>

  <!-- Start common custom event -->
  <h3>Common custom event</h3>
  <my-common-custom-event
    @no-validate-event="noValidateCallback"
    @validate-common-param-event="validateCommonParamCallback"
    @validate-object-param-event="validateObjectParamCallback"
  />
  <!-- End common custom event -->

  <!-- Start v-model default custom event -->
  <h3>v-model default 【eg. v-model="test"】 custom event</h3>
  <!-- v-model will auto handle update:modelValue event called by child components -->
  <my-model-default-custom-event v-model="title1" /> <!-- eqs to --> <!-- <my-model-default-custom-event v-model:modelValue="title1" /> -->
  {{title1}}
  <!-- End v-model default custom event -->

  <!-- Start v-model:attribute custom event -->
  <h3>v-model:attribute 【eg. v-model:title="test"】 custom event</h3>
  <!-- v-model:title will auto handle update:title event called by child components -->
  <my-model-attribute-custom-event
    v-model:title="title"
  />
  {{title}}
  <!-- End v-model:attribute custom event -->


  <!-- Start multiple v-model:attribute custom event -->
  <h3>Multiple v-model:attribute custom event</h3>
  <my-model-multiple-attribute-custom-event
    v-model:first-name="firstName"
    v-model:last-name= "lastName"
  />
  {{firstName}} - {{lastName}}
  <!-- End multiple v-model:attribute custom event -->

  <!-- Start modifiers -->
  <!-- v-model has built-in modifiers - .trim, .number and .lazy -->
  <h3>Handling v-model default 【eg. v-model.trim.my_capitalize="title"】 modifiers</h3>
  <my-model-default-custom-event-modifier v-model.trim.my_capitalize="testModifiers" />
    Value: {{testModifiers}}; Lenght: {{testModifiers.length}}

  <h3>Handling v-model:attribute 【eg. v-model:title.trim.my_capitalize="title"】 modifiers</h3>
  <my-model-attribute-custom-event-modifier v-model:testModifiers1.trim.my_capitalize="testModifiers1" />
    Value: {{testModifiers1}}; Lenght: {{testModifiers1.length}}
  <!-- End modifiers -->

</template>

<script>
import MyCommonCustomEvent from "./components/MyCommonCustomEvent.vue"
import MyModelDefaultCustomEvent from "./components/MyModelDefaultCustomEvent.vue"
import MyModelAttributeCustomEvent from "./components/MyModelAttributeCustomEvent.vue"
import MyModelMultipleAttributeCustomEvent from "./components/MyModelMultipleAttributeCustomEvent.vue"
import MyModelDefaultCustomEventModifier from "./components/MyModelDefaultCustomEventModifier.vue"
import MyModelAttributeCustomEventModifier from "./components/MyModelAttributeCustomEventModifier.vue"

export default {
  name: "App",
  data() {
    return {
      title: "",
      title1: "",
      firstName: "",
      lastName: "",
      testModifiers: "",
      testModifiers1: "",
    }
  },
  components: {
    MyCommonCustomEvent,
    MyModelDefaultCustomEvent,
    MyModelAttributeCustomEvent,
    MyModelMultipleAttributeCustomEvent,
    MyModelDefaultCustomEventModifier,
    MyModelAttributeCustomEventModifier,
  },
  methods: {
    noValidateCallback(event) {
      alert(event);
    },
    
    validateCommonParamCallback(event) {
      alert(event);
    },

    validateObjectParamCallback(event) {
      console.log(event);
    },
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
