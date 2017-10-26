<template lang="pug">

button.button(
	v-if="type === 'submit'"
	name='name'

    v-on:click="click"
	v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""'
)
	slot
a.button(
	v-else-if="type === 'link'"
	v-on:click="click"
	v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""'
)
	slot
div.button(
	v-else-if="(typeof (type))!== 'string' "

	v-on:click="click"
	v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""'
)
	slot
//template(v-else)
		//slot

</template>

<script>
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
        },
		methods: {
			click() {
				//console.log("click");
			}

		}
    }
</script>

<style lang="scss">
//цвет по умолчанию
$basecolors: (
	blue: #007aff,
);

$base-sizes: (
	//имя:padding-y, padding-x, font-size
	s: (8, 16, 12),
	m: (6, 24, 16),
	l: (12, 32, 20),
	xl:(16, 44,26)
);

@mixin button-mixin($basecolors, $base-sizes) {
    .button {
		position:relative; //для .ripped container
		border-width:2px;
		border-style:solid;
		//border: none;
		padding: 15px 32px;

		text-align: center;
		text-decoration: none;
		display: inline-block;
		color: #000;
		padding: 15px 32px;
		font-size: 16px;

		//модификаторы размеров кнокпки
		@each $name, $option in $base-sizes {
			&--size-#{$name} {
				padding: #{ nth($option,1)}px #{ nth($option,2)}px;
				font-size:#{ nth($option,3)}px;
				//color:red;

			}
		}

		//модификатор заркугленных углов
		&--round {
			border-radius: 1000px;
		}

		//модификатор с плоским стилем кнопки
		&--flat{
			border:none;
		}

		//модификатор с нажимающейся кнопки
		&--push{
			//border-bottom:-5px solid rgba(0,0,0,0.4);
			box-shadow: 0 -3px rgba(0,0,0,0.4) inset, 0 4px 6px 0 rgba(0,0,0,0.2), 0 2px 2px 0 rgba(0,0,0,0.19);

			//transform: translate(0, -2px);

			//box-shadow: 0px 8px 10px 0px rgba(0, 0, 0, .3), inset 0px 4px 1px 1px white, inset 0px -3px 1px 1px rgba(204,198,197,.5);
			&:active{
			box-shadow: none;
			}
		}

		//одификатор тени
		&--shadow:after{
			box-shadow: 0 4px 6px 0 rgba(0,0,0,0.2), 0 2px 2px 0 rgba(0,0,0,0.19);
			&-active:active{
			box-shadow: 0 4px 6px 0 rgba(0,0,0,0.2), 0 2px 2px 0 rgba(0,0,0,0.19);
			}
			&-hover:hover{
			box-shadow: 0 6px 8px 0 rgba(0,0,0,0.2), 0 3px 3px 0 rgba(0,0,0,0.19);
			}

		}

		//модификатор заполнения всего родительского пространства
		&--fill {
			width: 100%;
			height:100%;
			&-x{//по ширине
				width: 100%;
			}
			&-y{//по высоте
				height:100%;
			}
		}

		//задаем базовый цвет кнопок
		@each $name, $code in $basecolors {
			border-color: #{$code};
			border-width:2px;
			border-style:solid;

			color: #{$code};
			&:active, &.active-state {
				background-color: rgba($code, 0.3);
			}
			&:hover{
				background-color: rgba($code, 0.15);
			}
			&--active {
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

				&.button-fill{
					background-color: #{$code};
					color: white;
				}
					//модификатор неактивной кнопки
			&--disable{
				box-shadow:none !important;
				background-color: rgba($code, 0.15) !important;
			}
		}//конец звдвния базовых цветов

    }

}

@include button-mixin($basecolors, $base-sizes);

</style>
