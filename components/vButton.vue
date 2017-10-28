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
	//имя:padding-y, padding-x, height, width,  font-size
	s: (4px, 16px, auto, auto, 12px),
	m: (6px, 24px, auto, auto, 16px),
	l: (12px, 32px, auto, auto, 20px),
	xl: (16px, 44px, auto, auto,26px),
	s-icon: (5px, 5px, 22px, 22px, 12px),
	m-icon: (10px, 10px, 50px, 50px, 24px),
	l-icon: (22px, 22px, 74px, 74px, 30px),
	xl-icon: (25px, 25px, 100px, 100px,50px),
);

$border:2px;

@mixin button-mixin($basecolors, $base-sizes, $border) {
    .button {
		position:relative; //для .ripped container

		//border: none;
		padding: 15px 32px;

		vertical-align: middle;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		color: #000;
		padding: 15px 32px;
		font-size: 16px;

		//модификаторы размеров кнокпки
		@each $name, $option in $base-sizes {
			&--size-#{$name} {
				padding: #{ nth($option,1)} #{ nth($option,2)};
				height: #{ nth($option,3)};
				width: #{ nth($option,4)};
				font-size:#{ nth($option,5)};
			}
		}

		//модификатор заркугленных углов
		&--round{
			border-radius: 1000px;
			&-right{
				border-radius: 0 1000px 1000px 0;
			}
			&-left{
				border-radius: 1000px 0 0 1000px;
			}
		}

		//модификатор с плоским стилем кнопки
		&--flat{
			border:none;
		}

		//модификатор с нажимающейся кнопки
		&--push{
			//transform: translate(0, - (#{$border+3px}) );
			&:not(.button--active){
				border-bottom-width: #{$border+3px};
			}
			&:active:not(.button--active){
				border-bottom-width: #{$border};
				transform: translate(0, (#{$border+3px}));
				box-shadow: none;
			}

			&::before{
				content:"";
				position: absolute;
				top: 5px;
				left: 0;
				background-color: inherit;
				width:100%;
				height: 100%;
				border-radius: inherit;
				//opacity: 0.5;
				box-shadow:  0 -5px rgba(0,0,0,0.3) inset;
				z-index: -1;
			}
			&:active{
				transform: translate(0, 0);
				transform: translate(0, (#{$border+3px}) );
				box-shadow: none;
			}
			&:active::before{
				box-shadow: none;
				top: 0px;
			}
		}

		//одификатор тени
		&--shadow{
			box-shadow: 0 4px 6px 0 rgba(0,0,0,0.2), 0 2px 2px 0 rgba(0,0,0,0.19);
			&::before{
				box-shadow: 0 -5px rgba(0,0,0,0.3) inset, 0 4px 6px 0 rgba(0,0,0,0.2), 0 2px 2px 0 rgba(0,0,0,0.19);
			}
			&-active:active{// не работает!!!
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
			//&:not(&--active){
				border-color: #{$code};
				border-top-width:#{$border};
				border-left-width:#{$border};
				border-right-width:#{$border};
				border-bottom-width:#{$border};

				border-style:solid;
			//}
			color: #{$code};
					&:active, &.active-state {
						background-color: lighten($code,50%);// rgba($code, 0.3);
					}
					&:hover{
						background-color:lighten($code,40%);// rgba($code, 0.15);
					}
			&--active {
				border:none;
				background-color:  #{$code};
				//border:none;
				color:#fff;
					&:hover{
						background-color:  lighten($code,10%); //rgba($code, 0.85);
					}
					html:not(.watch-active-state) &:active, &.active-state {
						background-color: lighten($code,20%); //rgba($code, 0.7);
					}
       		}

			&.button-fill{
				background-color: #{$code};
				color: white;
				}
					//модификатор неактивной кнопки
			&--disable{
				box-shadow:none !important;
				background-color: lighten($code,20%) !important;//rgba($code, 0.15)
			}
		}//конец звдвния базовых цветов

    }

}

@include button-mixin($basecolors, $base-sizes, $border);

</style>
