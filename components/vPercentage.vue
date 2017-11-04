<template lang="pug">
div.percentage(v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("chart__" + o.split(" ").join(" chart__") ): "" ) : ""')
	svg.percentage_svg(v-bind:height='h' v-bind:width='w')
		circle.percentage_progress-bg(v-bind:cx='h/2' v-bind:cy='w/2' v-bind:r='h / 2 - strokeWidth' stroke="#e5e5e5" v-bind:stroke-width='strokeWidth' fill="none" )
		circle.percentage_progress(v-bind:cx='h/2' v-bind:cy='w/2' v-bind:r='h / 2 - strokeWidth' v-bind:stroke-width='strokeWidth' fill="none" v-bind:stroke-dashoffset='((100-p)*(h/2-strokeWidth)*2*3.14159 )/100' v-bind:stroke-dasharray='(h/2-strokeWidth)*2*3.14159')
	div.percentage_slot
		//p {{p}}%
		slot

</template>

<script>
    export default {
		props:{
			o: String,
			h:Number,
			w:Number,
			p:Number,
			strokeWidth:{type:Number, default:4}
		},// [ 'o', 'h','w','stroke-width','p' ],//o - прочие опции,
        data () {
            return {
                msg : "shiro"
            }
        },
        components: {
			//vBox,
			//vCell
        },
		methods: {


		}
    }
</script>

<style lang="scss">
.percentage{
	position: relative;
	//height: auto;
	text-align: center;
	vertical-align: middle;
	&_slot{
		display: inline-block;
		//text-align: center;
		//vertical-align: middle;
		position: absolute;
		//right: 50%;
		top: 50%;
	   // bottom: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		}
	&_svg{
		transform: rotate(-90deg);

		}
	&_progress{
			stroke: #007aff;
		}
	&__no-bg-stroke &_progress-bg{
		stroke: none;
		}
	&__bg &_progress-bg{
		fill: #e5e5e5;
		}
}
</style>
