<template>
<div id="app">
    <test-one> </test-one>
    <container h1="привет!">

        <p>текст 1</p>

		<vCol w="4">
			тест 1
		</vCol>

		<vCol w="8">
			тест 1
		</vCol>
    </container>

	<vGrid o="size gv10">
	тест 2
	</vGrid>


</div>


</template>

<script>
import testOne from '../components/test1.vue'
import container from '../components/container.vue'
import vCol from '../components/col.vue'
import vGrid from '../components/grid.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Добро пожаловать в Your Vue.js App'
    }
  },
  components:{
        testOne,
      container,
	  vCol,
	  vGrid
    }
}
</script>

<style lang="scss">
* {
    box-shadow:0 0 1px blue;
}
</style>
