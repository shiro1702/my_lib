<template lang="pug">
div.grid(v-bind:class = '"grid--" + o.split(" ").join(" grid--") ')
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

$breakpoints: (
	xs: 480,
	sm: 768,
	ms: 1024,
	md: 1280,
	lg: 1440,
	mg: 1680
);

$columns: (24);

$indents: (1, 2, 3, 4, 5, 10, 15, 20, 25, 30, 40, 50);

$htmlFontSize: 10;

@mixin default($breakpoints, $htmlFontSize) {
	* {
		box-sizing: border-box;
	}

	html,
	body {
		margin: 0;
		padding: 0;
		width: 100%;
		height: 100%;
		overflow-x: hidden;
	}

	html {
		font-size: #{$htmlFontSize}px;

		$size: $htmlFontSize - 0.5;
		@for $i from length($breakpoints) through 1 {
			@media (max-width: #{nth(map-values($breakpoints), $i)}px) {
				font-size: #{$size}px;
			}
			$size: $size - 0.5;
		}
	}
}

@mixin grid($breakpoints) {
    .grid {
        display: block;
		width: 100%;
		max-width: 100%;
		margin-left: auto;
		margin-right: auto;

		@each $name, $width in $breakpoints {
			@media (min-width: #{$width}px) {
				&--size,
				&--#{$name} {
					width: #{$width}px;
				}
			}
		}
    }

	.box {
		display: block;
		height: 100%;
		font-size: 0;
		text-align: left;
		vertical-align: top;

		&--left {
			text-align: left;
		}

		&--right {
			text-align: right;
		}

		&--center {
			text-align: center;
		}

		&--justify {
			text-align: justify;
			text-justify: newspaper;

			&::after {
				content: "";
				width: 100%;
				height: 0;
				display: inline-block;
				font-size: medium;
			}
		}

		&--top {
			&::before {
				content: "";
				height: 100%;
				width: 0;
				vertical-align: top;
				display: inline-block;
			}

			> .cell {
				vertical-align: top;
			}
		}

		&--middle {
			&::before {
				content: "";
				height: 100%;
				width: 0;
				vertical-align: middle;
				display: inline-block;
			}

			> .cell {
				vertical-align: middle;
			}
		}

		&--bottom {
			&::before {
				content: "";
				height: 100%;
				width: 0;
				vertical-align: bottom;
				display: inline-block;
			}

			> .cell {
				vertical-align: bottom;
			}
		}
	}

	.cell {
		display: inline-block;
		max-width: 100%;
		font-size: medium;
		text-align: left;
		vertical-align: top;

		&--left {
			text-align: left;
		}

		&--right {
			text-align: right;
		}

		&--center {
			text-align: center;
		}

		&--justify {
			text-align: justify;
			text-justify: newspaper;
		}

		&--top {
			vertical-align: top;
		}

		&--middle {
			vertical-align: middle;
		}

		&--bottom {
			vertical-align: bottom;
		}
	}

}

@mixin grid-column($columns, $breakpoints) {
	.grid--col#{$columns} {
		> .box > .cell--none,
		> .cell--none {
			display: none;
		}

		> .box > .cell--auto,
		> .cell--auto {
			display: inline-block;
			width: auto;
		}

		> .box > .cell--full,
		> .cell--full {
			display: inline-block;
			width: 100%;
		}

		@for $i from 1 through $columns {
			> .box > .cell--col#{$i},
			> .cell--col#{$i} {
				display: inline-block;
				width: ($i * 100% / $columns);
			}
		}

		@each $name, $width in $breakpoints {
			@media (max-width: #{$width}px) {
				> .box > .cell--#{$name}#{0},
				> .cell--#{$name}#{0} {
					display: none;
				}

				> .box > .cell--#{$name},
				> .cell--#{$name} {
					display: inline-block;
					width: auto;
				}

				@for $i from 1 through $columns {
					> .box > .cell--#{$name}#{$i},
					> .cell--#{$name}#{$i} {
						display: inline-block;
						width: ($i * 100% / $columns);
					}
				}
			}
		}
	}
}

@mixin grid-indent($indent, $htmlFontSize) {
	.grid {
		&--gv#{$indent} {
			> .box {
				margin-left: #{- $indent / $htmlFontSize}rem;
				margin-right: #{- $indent / $htmlFontSize}rem;
				margin-bottom: #{- 2 * $indent / $htmlFontSize}rem;
			}
			> .box > .cell,
			> .cell {
				padding-left: #{$indent / $htmlFontSize}rem;
				padding-right: #{$indent / $htmlFontSize}rem;
				padding-bottom: #{2 * $indent / $htmlFontSize}rem;
			}
		}

		&--g#{$indent} {
			> .box {
				margin-left: #{- $indent / $htmlFontSize}rem;
				margin-right: #{- $indent / $htmlFontSize}rem;
			}
			> .box > .cell,
			> .cell {
				padding-left: #{$indent / $htmlFontSize}rem;
				padding-right: #{$indent / $htmlFontSize}rem;
			}
		}

		&--v#{$indent} {
			> .box {
				margin-bottom: #{- 2 * $indent / $htmlFontSize}rem;
			}
			> .box > .cell,
			> .cell {
				padding-bottom: #{2 * $indent / $htmlFontSize}rem;
			}

		}
	}
}

@include default($breakpoints, $htmlFontSize);
@include grid($breakpoints);
@each $column in $columns {
	@include grid-column($column, $breakpoints);
}
@each $indent in $indents {
	@include grid-indent($indent, $htmlFontSize);
}
</style>
