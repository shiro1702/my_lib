<template>
<div id="app">
    <test-one> </test-one>
    <container h1="привет">

        <p>текст 1</p>
    </container>
</div>


</template>

<script>
import testOne from '../components/test1.vue'
import container from '../components/container.vue'


export default {
  name: 'app',
  data () {
    return {
      msg: 'Добро пожаловать в Your Vue.js App'
    }
  },
  components:{
        testOne,
      container
    }
}
</script>

<style lang="scss">
* {
    box-shadow:0 0 1px blue;
}
</style>
