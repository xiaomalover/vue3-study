<template>
  <img :src="result && result.imgUrl" />
</template>

<script>

    import axios from 'axios'

    export default {
        name: 'MyRemoteComponent',
       
        async setup() {            
            let rawData = await axios.get('https://apiblog.jspang.com/default/getGirl')
            return {result: rawData.data}
        },
    }
</script>
