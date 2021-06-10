<template>
  <div>
    <p class="success">{{result}}</p>
  </div>
</template>

<script>

export default {
  name: 'MyLocalComponent',
  async setup() {
    /**
     * This is the test to resolve.
     */
    return new Promise((resolve/* , reject */) => {
        setTimeout(function(){
            return resolve({result: "Local component data load successfull."})
        }, 3000)
    })

    /**
     * This is the test to reject, the parent component will capture and handle the error.
     */
    /* return new Promise((resolve, reject) => {
        setTimeout(function(){
            return reject({message: "Local component data load failed."})
        }, 3000)
    }) */
  }
}
</script>

<style scoped>
.success {
  color: green;
}
</style>