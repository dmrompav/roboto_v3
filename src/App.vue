<template lang="pug">
	.app
		.menu
			<transition :name="transName">
				ServiceNav(		v-if="centerWhichSelected===1 	&& isOpened" @ServiceNavButClick="ServiceNavButClick")
				BellabotNav(	v-if="centerWhichSelected===11 	&& isOpened")
				HolabotNav(		v-if="centerWhichSelected===12 	&& isOpened")
				PudubotNav(		v-if="centerWhichSelected===13 	&& isOpened")
				PuductorNav(	v-if="centerWhichSelected===14 	&& isOpened")
			</transition>
			button.central(@click="OpenNav")
				<transition name="nav-appearance">
					Service(	v-if="centerHovered===1" 	:isOpened="isOpened")
					Bellabot(	v-if="centerHovered===11" 	:isOpened="isOpened")
					Holabot(	v-if="centerHovered===12" 	:isOpened="isOpened")
					Pudubot(	v-if="centerHovered===13" 	:isOpened="isOpened")
					Puductor(	v-if="centerHovered===14" 	:isOpened="isOpened")
				</transition>
				.description(v-if="!isOpened")
					.h2 кликните
				.description(v-if="centerHovered===1 	&& isOpened")
					h2.h2 сервисные роботы
				.description(v-if="centerHovered===11 	&& isOpened")
					h2.h2 Bella Bot
					| Робот официант. Умный, самостоятельный,  вежливый и безопасный
				.description(v-if="centerHovered===12 	&& isOpened")
					h2.h2 Hola Bot
					| Робот по уборке посуды. Загрузка до 120кг. Бесконтактное обслуживание
				.description(v-if="centerHovered===13 	&& isOpened")
					h2.h2 Pudu Bot
					| Робот доставщик. Самый популярный. 6000 роботов в более чем 30 странах, более 500 городов используют робота.
				.description(v-if="centerHovered===14 	&& isOpened")
					h2.h2 Puductor
					| Роботы-дезинфекторы. Автоматизированная дезинфекция помещений сухим туманом и ультрафиолетом.
			
			<transition name="swipe-appearance">
				.swipe-circle(v-if="isOpened") 	&or; 
			</transition>

		<transition name="main-appearance">
			ServiceMain(	v-if="centerHovered===1" 	:isOpened="isOpened")
			BellabotMain(	v-if="centerHovered===11" 	:isOpened="isOpened")
			HolabotMain(	v-if="centerHovered===12" 	:isOpened="isOpened")
			PudubotMain(	v-if="centerHovered===13" 	:isOpened="isOpened")
			PuductorMain(	v-if="centerHovered===14" 	:isOpened="isOpened")
		</transition>
</template>

<script>
import Service from './components/centrals/Service.vue'
import Bellabot from './components/centrals/Bellabot.vue'
import Holabot from './components/centrals/Holabot.vue'
import Pudubot from './components/centrals/Pudubot.vue'
import Puductor from './components/centrals/Puductor.vue'

import ServiceNav from './components/navs/ServiceNav.vue'
import BellabotNav from './components/navs/BellabotNav.vue'
import HolabotNav from './components/navs/HolabotNav.vue'
import PudubotNav from './components/navs/PudubotNav.vue'
import PuductorNav from './components/navs/PuductorNav.vue'

export default {
	name: 'Menu',
	components: {
		Service, 
		Bellabot, 
		Holabot, 
		Pudubot, 
		Puductor,
		ServiceNav, 
		BellabotNav, 
		HolabotNav, 
		PudubotNav, 
		PuductorNav
	},
	props: [],
	data() {
		return {
			isOpened: '',
			centerHovered: 1,
			centerWhichSelected: 1,
			transName: 'nav-appearance'
		}
	},
	methods: {
		OpenNav() {
			(this.isOpened === '')?
				(this.isOpened = 'opened'):
				(this.isOpened = '')
		},
		ServiceNavButClick(i) {
			this.transName = 'nav-second-appearance'
			this.centerWhichSelected = i
			this.centerHovered = i
			console.log(this.centerWhichSelected)
		}
	},
}
</script>

<style lang="sass">
@import 'assets/_reset.sass'

@font-face
	font-family: Cyber
	src: url("https://assets.codepen.io/605876/Blender-Pro-Bold.otf")
	font-display: swap

.app
	font-family: Cyber, sans-serif

.menu
	position: absolute

	width: 100vw
	height: 95vh

	display: flex
	justify-content: center
	align-items: center

	color: #ffffff

	background-color: black

.central
	position: relative
	z-index: 2

	width: 300px
	height: 300px

	display: flex
	justify-content: center
	align-items: center

.description
	position: absolute
	top: 280px

	width: 100%

	text-align: center

.h2
	text-transform: uppercase

.swipe-circle
	position: absolute
	z-index: 2
	bottom: -10px

	width: 30px
	height: 30px
	background-color: #00bbdd
	border-radius: 50%

	display: flex
	justify-content: center
	align-items: center

	font-size: 22px
	padding-top: 5px

	&:before
		content: ''
		position: absolute
		width: 100%
		height: 100%
		background-color: #00bbdd
		border-radius: 50%

		opacity: 0.5
		animation: scale-circle-anim 1s ease 0s infinite alternate

	@keyframes scale-circle-anim
		0%
			width: 100%
			height: 100%
		100%
			width: 200%
			height: 200%

	&:after
		content: ''
		position: absolute
		width: 100%
		height: 100%
		background-color: #00bbdd
		border: 1px solid white
		border-radius: 50%

		opacity: 0.5
		animation: swipe-circle-anim 1s ease 0s infinite

	@keyframes swipe-circle-anim
		0%
			top: 0
		100%
			top: -40px



// TRANSITIONS =====================
.nav-appearance-enter
	width: 0
	transform: translate(0, -100px)
	opacity: 0
.nav-appearance-enter-active
	transition: width 0.2s ease, transform 0.2s ease 0.2s, opacity 0.2s ease 0.2s
.nav-appearance-enter-to
	width: 300px
	transform: translate(0, 0px)
	opacity: 1
.nav-appearance-leave
	width: 300px
	transform: translate(0, 0px)
	opacity: 1
.nav-appearance-leave-active
	transition: width 0.2s ease 0.2s, transform 0.2s ease, opacity 0.2s ease
.nav-appearance-leave-to
	width: 0
	transform: translate(0, 100px)
	opacity: 0

.nav-appearance-enter
	width: 0
	transform: translate(0, -100px)
	opacity: 0
.nav-appearance-enter-active
	transition: width 0.2s ease, transform 0.2s ease 0.2s, opacity 0.2s ease 0.2s
.nav-appearance-enter-to
	width: 300px
	transform: translate(0, 0px)
	opacity: 1
.nav-appearance-leave
	width: 300px
	transform: translate(0, 0px)
	opacity: 1
.nav-appearance-leave-active
	transition: width 0.2s ease 0.2s, transform 0.2s ease, opacity 0.2s ease
.nav-appearance-leave-to
	width: 0
	transform: translate(0, 100px)
	opacity: 0
</style>

