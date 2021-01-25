<template lang="pug">
	.bellabot
		.face-screen
			.brows
				.brows__brow.brows__brow_1
				.brows__brow.brows__brow_2
			.eye.eye_left
				.pupil.pupil__left
			.eye.eye_right
				.pupil.pupil__right
			.nose
			.mouth-1
			.mouth-2
			.mouth-3
			.mustaches
				.mustaches__mustache.mustaches__mustache_1
				.mustaches__mustache.mustaches__mustache_2
				.mustaches__mustache.mustaches__mustache_3
				.mustaches__mustache.mustaches__mustache_4
</template>

<script>
export default {
	name: 'Bellabot',
}
</script>

<style lang="sass" scoped>
.bellabot
	width: 300px
	height: 300px

	display: flex
	justify-content: center
	align-items: center

.face-screen
	position: relative
	width: 300px
	height: 200px
	background-color: #050510
	border: 1px solid grey

	display: flex
	justify-content: center
	align-items: center

.brows
	position: absolute
	top: 10%
	width: 100%
	transition: top 0.1s

	&__brow
		position: absolute
		width: 30px
		height: 10px
		border-radius: 5px
		background-color: #dddfff
		transition: transform 0.1s

		&_1
			position: absolute
			left: 30%


		&_2
			position: absolute
			right: 30%


.eye
	position: absolute
	top: 35%
	width: 100px
	height: 100px
	border-radius: 50%
	background-color: #dddfff

	display: flex
	justify-content: center
	align-items: center

	transform: scaleY(1)
	transition: transform 0.2s
	animation: blink 4s infinite 1s

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

.pupil
	position: absolute
	width: 75px
	height: 75px
	border-radius: 50%
	background-color: #050510

	animation: pupil-move 4s infinite

	@keyframes pupil-move
		0%
			transform: translate(0px)
		10%
			transform: translate(0px, 0px)
		12%
			transform: translate(-10px, -10px)
		30%
			transform: translate(-10px, -10px)
		32%
			transform: translate(10px, -10px)
		50%
			transform: translate(10px, -10px)
		52%
			transform: translate(0px)
		100%
			transform: translate(0px)

.nose
	position: absolute
	top: 65%
	width: 17px
	height: 12px
	border-radius: 5px 5px 10px 10px
	background-color: #dddfff

.mouth-1
	position: absolute
	top: 70%
	left: 41%
	width: 30px
	height: 30px
	border-radius: 50%
	border: 5px solid rgba(0, 0, 0, 0)
	border-bottom: 5px solid #dddfff
	border-right: 5px solid #dddfff
	transform: rotate(30deg)

.mouth-2
	position: absolute
	top: 70%
	right: 41%
	width: 30px
	height: 30px
	border-radius: 50%
	border: 5px solid rgba(0, 0, 0, 0)
	border-bottom: 5px solid #dddfff
	border-right: 5px solid #dddfff
	transform: rotate(60deg)

.mouth-3
	position: absolute
	top: 83%
	right: 45%
	width: 30px
	height: 0px
	border-radius: 0 0 50% 50%
	border: 5px solid #dddfff
	border-top: 0px
	transition: height 0.2s

.mustaches
	position: absolute
	bottom: 0
	width: 100%

	&__mustache
		position: absolute
		width: 15px
		height: 5px
		border-radius: 2px
		background-color: #dddfff

		&_1
			bottom: 15px
			left: 0
			transform: rotate(-15deg)
		&_2
			bottom: 30px
			left: 0
			transform: rotate(-5deg)
		&_3
			bottom: 15px
			right: 0
			transform: rotate(15deg)
		&_4
			bottom: 30px
			right: 0
			transform: rotate(5deg)

.bellabot:hover
	& .eye
		animation: none
		transform: scaleY(1.1)
	& .pupil
		animation: none
	& .brows
		top: 10px
	& .brows__brow_1
		transform: rotate(-10deg)
	& .brows__brow_2
		transform: rotate(10deg)
	& .mouth-3
		height: 20px
	

</style>
