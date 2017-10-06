<template>
<div id="app">
    <test-one> </test-one>
    <container>

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

</style>
