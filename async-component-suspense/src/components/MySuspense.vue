<template>
  <div>
    <h1>This is the suspense demo.</h1>

    <!-- Local component demo start -->
    <h4>Local async component:</h4>
    <div class="error" v-if="error">
      {{error}}
    </div>
    <suspense v-else>
      <template #default>
        <my-local-component />
      </template>

      <template #fallback>
        <p>Loading data from local component...</p>
      </template>
    </suspense>
    <!-- Local component demo end -->

    <!-- Remote component demo start -->
    <h4>Remote async component:</h4>
    <div class="error" v-if="error">
      {{error}}
    </div>
    <suspense v-else>
      <template #default>
        <my-remote-component />
      </template>

      <template #fallback>
        <p>Loading data from remote component...</p>
      </template>
    </suspense>
    <!-- Remote component demo end -->

  </div>
</template>

<script>

import {ref, onErrorCaptured, defineAsyncComponent} from 'vue'
import MyLocalComponent from './MyLocalComponent.vue'

export default {
  name: 'MySuspense',

  setup() {
    let error = ref(null)
    onErrorCaptured(e => {
      error.value = e.message
      return true // If return true, the error will throw out again, otherwise the error will stop throw out.
    })
    return {error}
  },

  components: {
    MyLocalComponent, //Local async component
    MyRemoteComponent: defineAsyncComponent(() => import("./MyRemoteComponent.vue")) //Remote async component
  }
}
</script>

<style scoped>
.error {
  color: red;
}
</style>
