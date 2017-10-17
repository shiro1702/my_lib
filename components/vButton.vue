<template lang="pug">

button.button(v-if="type === 'submit'" name='name' v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""') {{ text }}
	slot
a.button(v-else-if="type === 'link'"  v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""') {{ text }}
	slot
div.button(v-else-if="(typeof (type))!== 'string' " v-bind:class = '((typeof (o)) === "string" ) ? ( (o!=="") ? ("button--" + o.split(" ").join(" button--") ): "" ) : ""') {{ text }}
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
//вет по умолчанию
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
						//border-color:rgba(#fff, 1);
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
		}//конец звдвния базовых цветов

    }

}

@include button-mixin($basecolors, $base-sizes);

</style>
