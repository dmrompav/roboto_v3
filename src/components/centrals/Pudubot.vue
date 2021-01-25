<template lang="pug">
	.pudubot
		.face-screen
			.face-laughing
				.eye.eye_left
				.eye.eye_right
				.mouth
				.mouth-laugh
</template>

<script>
export default {
	name: 'Pudubot',
}
</script>

<style lang="sass" scoped>
.pudubot
	width: 300px
	height: 300px

	display: flex
	justify-content: center
	align-items: center

.face-screen
	position: relative
	width: 300px
	height: 170px
	background-color: #050510
	border: 1px solid grey

.face-laughing
	position: absolute
	width: 100%
	height: 100%

	display: flex
	justify-content: center
	align-items: center

.eye
	position: absolute
	top: 35%
	width: 60px
	height: 60px
	border-radius: 50%
	background-color: #dddfff
	animation: blink 4s infinite 1s

	transition: transform 0.2s

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

	&_left
		left: 5%

	&_right
		right: 5%

.mouth
	position: absolute
	top: 60%
	width: 60px
	height: 10px
	border-radius: 5px
	background-color: #dddfff

	transition: top 0.2s 0.2s, width 0.2s 0.2s

.mouth-laugh
	position: absolute
	z-index: 0
	top: 55%

	width: 42%
	height: 20%
	border-radius: 0 0 100px 100px
	background-color: #dddfff

	transform-origin: center 0%
	transform: scaleY(0)

	transition: transform 0.2s

.pudubot:hover
	& .face-laughing
		animation: laugh 8s infinite

		@keyframes laugh
			0%
				transform: translateY(0px)
			2%
				transform: translateY(-7px)
			5%
				transform: translateY(0px)
			7%
				transform: translateY(-7px)
			10%
				transform: translateY(0px)
			12%
				transform: translateY(-7px)
			15%
				transform: translateY(0px)
			17%
				transform: translateY(-7px)
			20%
				transform: translateY(0px)
			22%
				transform: translateY(-7px)
			25%
				transform: translateY(0px)
			27%
				transform: translateY(-7px)
			30%
				transform: translateY(0px)
			32%
				transform: translateY(-7px)
			35%
				transform: translateY(0px)
			37%
				transform: translateY(-7px)
			40%
				transform: translateY(0px)
			42%
				transform: translateY(-7px)
			45%
				transform: translateY(0px)
			47%
				transform: translateY(-7px)
			50%
				transform: translateY(0px)
			100%
				transform: translateY(0px)

	& .eye
		animation: none
		transform: scaleY(0.4)

	& .mouth
			top: 55%
			width: 40%
			transition: top 0.2s, width 0.2s

	& .mouth-laugh
		transform: scaleY(1)
		transition: transform 0.2s 0.2s


</style>
