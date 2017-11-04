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

$themecolor : #007aff;

@mixin theme-mixin($basecolors) {
    .theme {

		@each $name, $code in $basecolors {
			&--#{$name} .button{
					color: #{$code};
					html:not(.watch-active-state) &:active, &.active-state {
						background-color:  lighten($code,70%); //rgba($code, 0.3);
					}
					&:hover{
						background-color: lighten($code,85%); //rgba($code, 0.15);
					}
					&.button--active {
						background-color: #{$code};
						border:none;
						color:#fff;
							&:hover{
								background-color:  lighten($code,10%); //rgba($code, 0.85);
							}
							html:not(.watch-active-state) &:active, &.active-state {
								background-color: lighten($code,20%); //rgba($code, 0.7);
							}

        			}
					&.button--disable{
						box-shadow:none  !important;
						background-color:lighten($code,20%) !important; //; rgba($code, 0.5)
					}
					&:not(.button--flat):not(.button--active){
						border-color: #{$code};
						//border-width:2px;
						border-style:solid;
					}
				}
			&--#{$name} .percentage{
				&_progress{
					stroke:#{$code};
				}

			}


		}
    }

}

@include theme-mixin($basecolors);

</style>
