<template>
<div id="app">


	<vTheme>
	</vTheme>
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

	<vGrid o="col24 mg md md ms sm st"> <!-- o="t size gv10"-->
	тест 2
		<vBox o ="middle">
			<vCell o="full">
				тест 3
			</vCell>
			<vCell o ="col1">
				тест 4
			</vCell>
			<vCell o ="col18">
				<p> тест 5 </p>
				<p> тест 5 </p>
			</vCell>
			<vCell o ="col5"  class="theme--red">
				<vButton type="link" href="#" o=""> тест 6</vButton>
			</vCell>
		</vBox>
	</vGrid>


</div>


</template>

<script>
import testOne from '../components/test1.vue'
import container from '../components/container.vue'
import vCol from '../components/col.vue'

import vGrid from '../components/vGrid.vue'
import vBox from '../components/vBox.vue'
import vCell from '../components/vCell.vue'

import vButton from '../components/vButton.vue'

import vTheme from '../components/vTheme.vue'


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
	  vGrid, vBox, vCell,

	  vButton,
	  vTheme
    }
}
</script>

<style lang="scss">
* {
    box-shadow:0 0 1px blue;
}
</style>
