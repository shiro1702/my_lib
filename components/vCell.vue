<template lang="pug">
div.cell(v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("cell--" + o.split(" ").join(" cell--") ): "" ) : ""')
	//p {{ 'grid--' + o.split(' ').join(' grid--') }}
	slot
</template>

<script>
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
        }
    }
</script>

<style lang="scss">

</style>
