<template lang="pug">

button.button(v-if="type === 'submit'" name='name' v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("btn--" + o.split(" ").join(" btn--") ): "" ) : ""') {{ text }}
	slot
a.button(v-else-if="type === 'link'"  v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("btn--" + o.split(" ").join(" btn--") ): "" ) : ""') {{ text }}
	slot
div.button(v-else-if="(typeof (type))!== 'string' " v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("btn--" + o.split(" ").join(" btn--") ): "" ) : ""') {{ text }}
	slot
//template(v-else)
		//slot

</template>

<script>
//import vCell from '../components/cell.vue'

    export default {
		props: [ 'o', 'type' ],
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
$basecolors: (
	green: #4CAF50,
	blue: #008CBA,
	red: #f44336,
	orange: #FF5300,
	yellow: #FFED00,
	gray: #e7e7e7,
	black: #555555,
	white: #fff,
	purple: #5A009D
);


@mixin button-mixin($basecolors) {
    .button {

		border: none;

		padding: 15px 32px;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		color: #000;
		font-size: 16px;

		width: 100%;

		@each $name, $code in $basecolors {
				&--color-#{$name} {
					background-color: #{$code};
					color: white;
				}
		}

		@each $name, $code in $basecolors {
				&--border-#{$name} {
					//background-color: #{$code};
				    //background-color: white;
					color: #{$code};// black;
					border: 2px solid #{$code}; /* Green */
				}

		}
    }

}

@include button-mixin($basecolors);

</style>
