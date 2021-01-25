<template lang="pug">
	.app
		.menu
			.nav-after(v-if="isOpened" @click="OpenNav") X
			.tapfield(@click="OpenNav")
			<transition name="nav-appearance">
				ServiceNav(		v-if="centerWhichSelected===1 	&& isOpened" @ServiceNavButClick="ServiceNavButClick" @hovered="Hovered" @nonhovered="NonHovered")
			</transition>
			button#central.central(@click="OpenNav")
				<transition name="center-appearance">
					Service(	v-if="centerHovered===1" 	:isOpened="isOpened")
					Bellabot(	v-if="centerHovered===11" 	:isOpened="isOpened")
					Holabot(	v-if="centerHovered===12" 	:isOpened="isOpened")
					Pudubot(	v-if="centerHovered===13" 	:isOpened="isOpened")
					Puductor(	v-if="centerHovered===14" 	:isOpened="isOpened")
				</transition>
				.description(v-if="!isOpened && centerWhichSelected===1")
					.h2 кликните
				.description(v-if="centerHovered===1 	&& isOpened")
					h2.h2 сервисные роботы
				.description(v-if="centerHovered===11")
					h2.h2 Bella Bot
					| Робот официант. Умный, самостоятельный,  вежливый и безопасный
				.description(v-if="centerHovered===12")
					h2.h2 Hola Bot
					| Робот по уборке посуды. Загрузка до 120кг. Бесконтактное обслуживание
				.description(v-if="centerHovered===13")
					h2.h2 Pudu Bot
					| Робот доставщик. Самый популярный. 6000 роботов в более чем 30 странах, более 500 городов используют робота.
				.description(v-if="centerHovered===14")
					h2.h2 Puductor
					| Роботы-дезинфекторы. Автоматизированная дезинфекция помещений сухим туманом и ультрафиолетом.
			<transition name="nav-appearance">
				BellabotNav(	v-if="centerWhichSelected===11 	&& isOpened" @abort="abort")
				HolabotNav(		v-if="centerWhichSelected===12 	&& isOpened" @abort="abort")
				PudubotNav(		v-if="centerWhichSelected===13 	&& isOpened" @abort="abort")
				PuductorNav(	v-if="centerWhichSelected===14 	&& isOpened" @abort="abort")
			</transition>
			<transition name="swipe-appearance">
				a(href="#central").swipe-circle(v-if="centerWhichSelected > 10 || isOpened")
			</transition>
		
		<transition name="main-appearance">
			BellabotMain(	v-if="centerWhichSelected===11" 			:isOpened="isOpened")
		</transition>
		<transition name="main-appearance">
			HolabotMain(	v-if="centerWhichSelected===12" 			:isOpened="isOpened")
		</transition>
		<transition name="main-appearance">
			PudubotMain(	v-if="centerWhichSelected===13" 			:isOpened="isOpened")
		</transition>
		<transition name="main-appearance">
			PuductorMain(	v-if="centerWhichSelected===14" 			:isOpened="isOpened")
		</transition>
		<transition name="main-appearance">
			ServiceMain(	v-if="centerWhichSelected>=10 || isOpened"	:isOpened="isOpened")
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

import ServiceMain from './components/mains/ServiceMain.vue'
import BellabotMain from './components/mains/BellabotMain.vue'
import HolabotMain from './components/mains/HolabotMain.vue'
import PudubotMain from './components/mains/PudubotMain.vue'
import PuductorMain from './components/mains/PuductorMain.vue'

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
		PuductorNav,
		ServiceMain, 
		BellabotMain, 
		HolabotMain, 
		PudubotMain, 
		PuductorMain,
	},
	props: [],
	data() {
		return {
			isOpened: '',
			centerHovered: 1,
			centerWhichSelected: 1,
		}
	},
	methods: {
		OpenNav() {
			(this.isOpened === '')?
				(this.isOpened = 'opened'):
				(this.isOpened = '')
				console.log(this.centerWhichSelected)
		},
		ServiceNavButClick(i) {
			this.centerWhichSelected = i
			this.centerHovered = i
			console.log(this.centerWhichSelected)
		},
		abort() {
			this.centerWhichSelected = (this.centerWhichSelected -this.centerWhichSelected % 10) / 10
			this.centerHovered = this.centerWhichSelected
			console.log(this.centerWhichSelected - this.centerWhichSelected % 10)
		},
		Hovered(i) {
			this.centerHovered = i
		},
		NonHovered() {
			this.centerHovered = this.centerWhichSelected
		}
	},
}
</script>

<style lang="sass">
@import 'assets/_reset.sass'
@import 'assets/_glitch.sass'
@import 'assets/_nav-buttons.sass'

@font-face
	font-family: Cyber
	src: url("https://assets.codepen.io/605876/Blender-Pro-Bold.otf")
	font-display: swap

html
	scroll-behavior: smooth

body
	width: 100vw
	overflow-x: hidden
	color: #ffffff
	background-color: #000000

.app
	font-family: Cyber, sans-serif

	display: flex
	flex-direction: column
	justify-content: center
	align-items: center

.menu
	position: relative

	width: 100vw
	height: 95vh

	display: flex
	justify-content: center
	align-items: center


	background-color: black

.tapfield
	position: absolute
	top: 0
	left: 0
	width: 0
	height: 0
	@media (max-width: 710px)
		width: 100vw
		height: 100vh
.nav
	z-index: 1
	background-color: #000

	@media (max-width: 710px)
		position: absolute
	
.nav-after
	display: none

	@media (max-width: 710px)
		display: block
		position: absolute
		right: 20px
		top: 20px
		font-size: 50px
		color: #fff

.central
	position: relative
	z-index: 0

	width: 300px
	height: 300px
	margin: 0 50px

	display: flex
	justify-content: center
	align-items: center

	@media (max-width: 710px)
		position: absolute

.description
	position: absolute
	top: 280px

	width: 100%

	font-size: 20px
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

.main-appearance-enter
	transform: translate(0, 100px)
	opacity: 0
.main-appearance-enter-active
	transition: transform 0.2s, opacity 0.2s
.main-appearance-enter-to
	transform: translate(0, 0px)
	opacity: 1
.main-appearance-leave
.main-appearance-leave-active
.main-appearance-leave-to


// .center-appearance-enter
// 	opacity: 0
// .center-appearance-enter-active
// 	transition: opacity 0.2s
// .center-appearance-enter-to
// 	opacity: 1
// .center-appearance-leave
// 	opacity: 1
// .center-appearance-leave-active
// .center-appearance-leave-to
// 	opacity: 0
</style>

