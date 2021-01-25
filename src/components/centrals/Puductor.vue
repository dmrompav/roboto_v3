<template lang="pug">
	.puductor(@mouseenter="PuductorHard" @mouseleave="PuductorEasy")
		.hard-lamp(v-if="hardClass === 1")
		.face-screen
			.eye.eye__left
			.eye.eye__right

</template>

<script>
export default {
	name: 'Puductor',
	data() {
		return {
			hardClass: 0
		}
	},
	methods: {
		PuductorHard() {
			this.hardClass = 1
		},
		PuductorEasy() {
			this.hardClass = 0
		}
	}
}
</script>

<style lang="sass" scoped>
.puductor
	width: 100%
	height: 100%

	display: flex
	justify-content: center
	align-items: center

	&:hover
		& .eye
			animation: shake 0.1s infinite
			height: 30px
			transition: transform 0.2s

			@keyframes shake
				0%
					transform: translate(-2px)
				50%
					transform: translate(2px)
				100%
					transform: translate(-2px)

.hard-lamp
	position: absolute
	width: 100%
	height: 50%

	animation: lamp-start 1s infinite

	@keyframes lamp-start 
		0%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		18%
			box-shadow: 0 0 5px #dddfff, 0 0 10px #dddfff, 0 0 30px #dddfff, 0 0 40px #dddfff, 0 0 100px 20px #00e0ff 
		20%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		22%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		40%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		42%
			box-shadow: 0 0 5px #dddfff, 0 0 10px #dddfff, 0 0 30px #dddfff, 0 0 40px #dddfff, 0 0 100px 20px #00e0ff 
		44%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		72%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		74%
			box-shadow: 0 0 5px #dddfff, 0 0 10px #dddfff, 0 0 30px #dddfff, 0 0 40px #dddfff, 0 0 100px 20px #00e0ff 
		84%
			box-shadow: 0 0 5px #dddfff, 0 0 10px #dddfff, 0 0 30px #dddfff, 0 0 40px #dddfff, 0 0 100px 20px #00e0ff 
		98%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 
		100%
			box-shadow: 0 0 10px #dddfff, 0 0 20px #dddfff, 0 0 40px #dddfff, 0 0 80px #dddfff, 0 0 160px 20px #00e0ff 

.face-screen
	position: absolute
	width: 100%
	height: 70%
	border: 1px solid grey
	background-color: #050510

	display: flex
	justify-content: center
	align-items: center

.eye
	position: absolute
	width: 60px
	height: 160px
	background-color: #dddfff
	border-radius: 20px

	animation: blink 4s infinite 0s
	transform: scaleY(1)
	transition: height 0.2s

	@keyframes blink
		0%
			transform: scaleY(1)
		4%
			transform: scaleY(0.2)
		6%
			transform: scaleY(1)
		8%
			transform: scaleY(1)
		12%
			transform: scaleY(0.2)
		14%
			transform: scaleY(1)
		100%
			transform: scaleY(1)

	&__left
		left: 40px

	&__right
		right: 40px
</style>
