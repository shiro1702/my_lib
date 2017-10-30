<template lang="pug">
div
	svg(v-bind:height='h' v-bind:width='w' class="skill-item__svg")
		circle.progress(v-bind:cx='h/2' v-bind:cy='w/2' v-bind:r='h / 2 - strokeWidth' stroke="#b2b2b2" v-bind:stroke-width='strokeWidth' fill="none" v-bind:stroke-dashoffset='((100-p)*(h/2-strokeWidth)*2*3.14159 )/100' v-bind:stroke-dasharray='(h/2-strokeWidth)*2*3.14159')

	p % = {{p}}
	p ( (100-p)*h*3.14159 )/100 =  {{ ( (100-p)*h*3.14159 )/100 }}
	//slot
//template(v-else)
		//slot

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

skill-item__svg{
    position: absolute;
    right: 0;
    top: 0;
    bottom: 0;
    left: 0;
}

</style>
