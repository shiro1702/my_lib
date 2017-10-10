<template lang="pug">
div.v-col(v-bind:class = '"v-col_col-w_"+w')
	slot
</template>

<script>
    export default {
		props: ['w'],
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

.v-col {
	margin: 0 auto;
	width:100%;
	color:green;
	height:50px;
	&:after{
		clear: both;
		content: "";
		display: table;
	}
}

@for $i from 0 to 13 {
	.v-col_col-w_#{$i}
		{
		color:red;
		width: (100%*$i/12); //расчитываем количество процентов
		float:left;
		}

}
</style>
