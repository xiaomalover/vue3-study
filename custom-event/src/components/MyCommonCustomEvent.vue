<template>
  <div>
    <p>
      <button @click="$emit('noValidateEvent')">
        No validate Event without param
      </button>
    </p>
    <p>
      <button @click="$emit('noValidateEvent', 'test params')">
        No validate Event with param
      </button>
    </p>
    <p>
      <button @click="$emit('validateCommonParamEvent', 'test params')">
        Validate Event with common param
      </button>
    </p>
    <p>
      <button @click="$emit('validateCommonParamEvent')">
        Validate Event without common param
      </button>
    </p>
    <p>
      <button @click="$emit('validateObjectParamEvent', {username: 'Zhan san', password: 'Aa123456'})">
        Validate Event with object param
      </button>
    </p>
    <p>
      <button @click="$emit('validateObjectParamEvent',  {username: 'Zhan san', password: ''})">
        Validate Event without object param
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: "MyCommonCustomEvent",

  /**
   * Emits use array can't validate event.
   */
  //emits: ['noVaildateEvent', 'test']

  /**
   * Emits use object can validate event.
   */
  emits: {

    noValidateEvent: null,

    validateCommonParamEvent: (params) => {
      if (!params) {
        console.warn("params can't be null")
        return false
      }
      return true
    },

    validateObjectParamEvent: ({username, password}) => {
      if (!username || !password) {
        console.warn("params error")
        return false
      }
      return true
    }
  },
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
