<template>
  <div>
    <h1> This is the demo for props </h1>

    <!-- Start props type use basic -->
    <h3>
      Props Types Basic(String,Number,Boolean,Array,Object,Date,Function,Symbol)
    </h3>
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
      :staticObject="{ name: 'Zhang san', age: 33 }"
      :dynamicObject="post.author"
      v-bind="allObject"
    />
    <!-- End props type use basic -->

    <!-- Start props validate -->
    <h3>Prop Validate</h3>
    <my-props-validate
      :number-prop="888"
      multiple-prop="Can be number or string, I'm string now."
      required-string-prop="I'm required string"
      custom-validator-prop="danger"
    />
    <!-- End props validate -->

    <!-- Start none props attribute -->
    <h3>Non-Prop Attributes(class, style, id)</h3>
    <my-one-root-class-attribute data-status="activated"></my-one-root-class-attribute>
    <my-one-root-on-event-attribute @change="showChange"></my-one-root-on-event-attribute>
    <my-one-root-bind-child data-status="activated"></my-one-root-bind-child>
    <my-multiple-root-class-attribute data-status="activated"></my-multiple-root-class-attribute>
    <!-- End none props attribute -->
  </div>
</template>

<script>
import MyProps from "./components/MyProps.vue"
import MyPropsValidate from "./components/MyPropsValidate.vue"
import MyOneRootClassAttribute from "./components/none-prop-attribute/MyOneRootClassAttribute.vue"
import MyOneRootOnEventAttribute from "./components/none-prop-attribute/MyOneRootOnEventAttribute.vue"
import MyOneRootBindChild from "./components/none-prop-attribute/MyOneRootBindChild.vue"
import MyMultipleRootClassAttribute from "./components/none-prop-attribute/MyMultipleRootClassAttribute.vue"

export default {
  name: "App",
  data() {
    return {
      post: {
        title: "This is dynamic string value",
        id: 1,
        isNew: false,
        keywords: ["hot", "new", "recommend"],
        author: { name: "Li si", age: 44 },
      },
      allObject: {
        allObjectAttr1: "string",
        allObjectAttr2: 1,
        allObjectAttr3: false,
      },
    };
  },
  components: {
    MyProps,
    MyPropsValidate,
    MyOneRootClassAttribute,
    MyOneRootOnEventAttribute,
    MyOneRootBindChild,
    MyMultipleRootClassAttribute
  },

  methods: {
    showChange(event) {
      console.log(event.target.value)
    }
  }

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
