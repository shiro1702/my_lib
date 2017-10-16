<template lang="pug">
div
	slot

</template>

<script>
    export default {
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
$basecolors: (
	blue: #007aff,
	green: #4CAF50,
	red: #ff3b30,

	orange: #ff9500,
	yellow: #ffcc00,
	gray: #8e8e93, /*#e7e7e7,*/
	black: #555555,
	white: #ffffff,
	purple: #5A009D
);

$themecolor : blue;

@mixin theme-mixin($basecolors) {
    .theme {

		@each $name, $code in $basecolors {
				&--#{$name} .button:not(.button-fill){
					border-color: #{$code};
					color: #{$code};
					html:not(.watch-active-state) &:active, &.active-state {
						//background-color: #{$code};
						//background-opasity:
						background-color: rgba($code, 0.15);
						//background-color: transparentize(#{$code}, 0.15);
					}
					&.active {
						background-color:  #{$code};
						color:#fff;
        			}
				}

				&--#{$name} .button-fill{
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

@include theme-mixin($basecolors);

</style>
