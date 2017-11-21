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
			<vCell o ="col5" class="theme--red">
				тест 4
				<vChart h="100" w="100" strokeWidth="10" v-bind:chartData='chartData' >
				</vChart>
			</vCell>
			<vCell o ="col5">
				<vButton type="link" href="#" o="size-m fill-x round push shadow"> тест 6</vButton>
			</vCell>
			<vCell o ="col5" >
				<vButton v-ripple.mat="true" type="link" href="#" o="size-m fill-x active shadow push">
					тест 6
				</vButton>
			</vCell>
			<vCell o ="col5"  class="theme--orange">
				<vButton v-ripple.mat="true" type="link" href="#" o="disable size-m fill-x active round shadow push"> тест 6</vButton>
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

import vChart from '../components/vChart.vue'
import vPercentage from '../components/vPercentage.vue'

import vTheme from '../components/vTheme.vue'

import Ripple from '../directives/ripple'


export default {
  name: 'app',
  data () {
    return {
      msg: 'Добро пожаловать в Your Vue.js App',
		chartData:[{
				color: "red",
				pVal:33.33,
				text: 'данные отсутсвуют.'
			},
			{
				color: "green",
				pVal:33.33,
				text: 'данные отсутсвуют.'
			},
			{
				color: "blue",
				pVal:33.33,
				text: 'данные отсутсвуют.'
			}
				  ]
    }
  },
	directives: {
			Ripple
		},
  components:{
        testOne,
      container,
	  vCol,
	  vGrid, vBox, vCell,

	  vButton, vChart,
	  vTheme
    }
}
</script>

<style lang="scss">
@import "directives/ripple";

* {
    box-shadow:0 0 1px blue;
}
</style>
