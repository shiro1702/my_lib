<template lang="pug">
div.box(v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("box--" + o.split(" ").join(" box--") ): "" ) : ""')
	//p {{ 'grid--' + o.split(' ').join(' grid--') }}
	slot
</template>

<script>
//import vCell from '../components/cell.vue'

    export default {
		props: {
			o: {
				type: Array,
				default: function () {
					return { o: 'привет!' }
					}
			},
			//.map(function(i) {return "grid--"+i;});
		},
        data () {
            return {
                msg : "shiro"
            }
        },
        components: {
			//vBox,
			//vCell
        }
    }
</script>

<style lang="scss">

</style>
