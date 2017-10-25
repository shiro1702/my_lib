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
			&--#{$name} .button{
					color: #{$code};
					html:not(.watch-active-state) &:active, &.active-state {
						background-color: rgba($code, 0.3);
					}
					&:hover{
						background-color: rgba($code, 0.15);
					}
					&.button--active {
						background-color:  #{$code};
						border:none;
						color:#fff;
							&:hover{
								background-color: rgba($code, 0.85);
							}
							html:not(.watch-active-state) &:active, &.active-state {
								background-color: rgba($code, 0.7);
							}

        			}
				}
			&--#{$name} .button:not(.button--flat):not(.button--active){
					border-color: #{$code};
					border-width:2px;
					border-style:solid;
				}

		}
    }

}

@include theme-mixin($basecolors);

</style>
