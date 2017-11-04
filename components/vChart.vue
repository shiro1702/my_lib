<template lang="pug">
div.chart(v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("chart__" + o.split(" ").join(" chart__") ): "" ) : ""')
	svg.chart_svg(v-bind:height='h' v-bind:width='w')
		circle.chart_progress-bg(v-bind:cx='h/2' v-bind:cy='w/2' v-bind:r='h / 2 - strokeWidth' stroke="#e5e5e5" v-bind:stroke-width='strokeWidth' fill="none" )

		circle(v-for='item, i in preProc' v-bind:cx='h/2' v-bind:cy='w/2' v-bind:r='h / 2 - strokeWidth' v-bind:stroke-width='strokeWidth' fill="none" v-bind:stroke='item.color' v-bind:stroke-dashoffset='(-item.pre *(h/2-strokeWidth)*2*3.14159 )/100' v-bind:stroke-dasharray='((item.pVal)*(h/2-strokeWidth)*2*3.14159 )/100+", "+(h/2-strokeWidth)*2*3.14159')
	div.chart_slot
		//p {{chartData.0.text}}
		slot

</template>

<script>
    export default {
		props:{
			o: String,
			h:Number,
			w:Number,
			p:Number,
			strokeWidth:{type:Number, default:4},
			chartData:{
				Type:Object,
				default: function () {
        		return [{
							color: "#000",
							pVal:0,
							text: 'данные отсутсвуют.'
					   }]
				}
			}
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
		methods: {//((i-1)<0)?0:(-chartData[i-1].pVal)


		},
		computed: {
			preProc: function () {
				var pro=[];
				var s=0;

				for (var item of this.chartData)
					{
						//alert(s+"::"+item.pVal);
						item.pre=s;
						pro.push(item);
						s=s+item.pVal;
					}
			  // `this` указывает на экземпляр vm
			  //this.chartData[i].pVal
				//alert(pro);
				return pro;
			}
		  }
		}
</script>

<style lang="scss">
.chart{
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
