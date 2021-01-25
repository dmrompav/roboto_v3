<template lang="pug">
	footer.footer
		section.footer__section.footer__section_1
			.container.flex-cont
				
				.pre-slider
					h3.footer__h3 Не можете выбрать?
					.footer__form-description Оставьте Ваши контактные данные и наши специалисты свяжутся с Вами
					.footer__form
						form#form
						input.input(type="text" placeholder="Ваше имя")
						input.input(type="tel" placeholder="Телефон")
					.footer__form
						.button-check.r#button-3
							input.checkbox(form="#form" type="checkbox" checked)
							.knobs
							.layer
						p.checkbox-p 
							span Я даю согласие на обработку персональных данных
					button.button.cybr-btn.submit(type="submit") Отправить
						span.cybr-btn__glitch(aria-hidden) Отправить
				.slider
					.slider__img.slider__img_1
					.slider__img.slider__img_2
					.slider__img.slider__img_3
					.slider__img.slider__img_4
		section.footer__section.footer__section_2
			.container
				h3.footer__h3 Наши контакты
				span.footer__contacts {{contact}}
				.footer__icons 
					.footer__icon.footer__icon_1(@click="()=>{this.contact = contacts[0]}")
					.footer__icon.footer__icon_2(@click="()=>{this.contact = contacts[1]}")
					.footer__icon.footer__icon_3(@click="()=>{this.contact = contacts[2]}")
					a(href="#" targey="_blank")
						.footer__icon.footer__icon_4
					a(href="#" targey="_blank")
						.footer__icon.footer__icon_5
					a(href="#" targey="_blank")
						.footer__icon.footer__icon_6
					a(href="#" targey="_blank")
						.footer__icon.footer__icon_7
				

</template>

<script>
export default {
	name: 'ServiceMain',
	data() {
		return {
			contact: '------',
			contacts: [
				'450071, г.Уфа, ул. Менделеева, 134/7, 4 этаж ',
				'zakaz@soft-servis.ru',
				'+7 (347) 222-20-21 '
			]
		}
	}
}
</script>

<style	lang="sass" scoped>
.container
	position: relative
	width: 95vw
	max-width: 1200px
	margin: 0 auto 10px auto
	padding: 40px 30px 10px 30px

	background-color: #fff
	color: #000000

.flex-cont
	display: flex
	flex-wrap: wrap
	justify-content: space-between

.footer
	width: 100vw

	&__section
		width: 100%
		&_1
		&_2

	&__h3
		font-size: 40px
	&__form-description
		font-size: 18px
		color: #777777
	&__form
		height: 50px
		margin: 20px 0 20px 0
		display: flex
		justify-content: flex-start
		align-items: center

	&__contacts
		font-size: 26px

	&__icons
		display: flex
		align-items: center
		justify-content: flex-start
		flex-wrap: wrap

	&__icon
		margin: 10px
		width: 50px
		height: 50px
		background-size: 700%
		background-image: url('../../assets/sprites.png')
		cursoir: pointer

		&_1
		&_2
			background-position: -100px
		&_3
			background-position: -200px
		&_4
			background-position: -300px
		&_5
			background-position: -400px
		&_6
			background-position: -500px
		&_7
			background-position: -600px



.input
	width: 120px
	height: 30px
	border: 1px solid grey
	margin: 0 20px 0 0
	padding-left: 10px
	transition: box-shadow 0.2s, width 0.2s, height 0.2s
	font-size: 18px

	&:hover
		height: 50px

	&:focus
		box-shadow: inset 0 0 5px #00bbdd, inset 0 0 10px #00bbdd
		height: 50px
		width: 180px

.submit
	width: 180px
	height: 40px
	line-height: 40px
	color: #fff
	font-size: 20px
	background-color: #00bbdd

.checkbox-p
	height: 30px
	margin-left: 15px

	display: flex
	align-items: center
	justify-content: flex-start

.slider
	position: relative
	right: 0
	top: 0
	width: 160px
	height: 300px

	&__img
		position: absolute
		width: 100%
		height: 100%
		opacity: 0
		animation: change-image 16s infinite
		background-size: 100%
		background-repeat: no-repeat

		&_1
			background-image: url(../../assets/puductor.jpg)
			animation-delay: 12s

		&_2
			background-image: url(../../assets/pudu.jpg)
			animation-delay: 8s

		&_3
			background-image: url(../../assets/hola.jpg)
			animation-delay: 4s

		&_4
			background-image: url(../../assets/bella.jpg)
			animation-delay: 0s

		@keyframes change-image
			0%
				opacity: 1
				transform: translate(0px)
			15%
				opacity: 1
				transform: translate(0px)
			20%
				opacity: 0
				transform: translate(-50px)
			90%
				opacity: 0
				transform: translate(0px)
			95%
				opacity: 1
				transform: translate(0px)
			100%
				opacity: 1
				transform: translate(0px)



// styled checkbox
*
	user-select: none
	-webkit-tap-highlight-color: transparent

	&:focus
		outline: none

.knobs, .layer
	position: absolute
	top: 0
	right: 0
	bottom: 0
	left: 0

.button-check
	position: relative
	width: 74px
	height: 36px
	overflow: hidden

	&.r
		border-radius: 100px

		.layer
			border-radius: 100px

.checkbox
	position: relative
	width: 100%
	height: 100%
	padding: 0
	margin: 0
	opacity: 0
	cursor: pointer
	z-index: 3

.knobs
	z-index: 2

.layer
	width: 100%
	background-color: #ebf7fc
	transition: 0.3s ease all
	z-index: 1

#button-3
	.knobs:before
		content: 'Да'
		position: absolute
		top: 4px
		left: 4px
		width: 28px
		height: 28px
		color: #fff
		font-size: 14px
		font-weight: bold
		text-align: center
		line-height: 12px
		padding: 9px 4px
		background-color: #00bbdd
		border-radius: 50%
		transition: 0.3s ease all, left 0.3s cubic-bezier(0.18, 0.89, 0.35, 1.15)

	.checkbox
		&:active + .knobs:before
			width: 46px
			border-radius: 100px

		&:checked
			&:active + .knobs:before
				margin-left: -26px

			+ .knobs:before
				content: 'Нет'
				left: 42px
				background-color: red

			~ .layer
				background-color: #fcebeb

</style>