<template lang="pug">
	.holabot
		.face-screen
			.eye.eye__left
			.eye.eye__right
</template>

<script>
export default {
	name: 'Holabot',
}
</script>

<style lang="sass" scoped>
.holabot
	position: relative
	width: 100%
	height: 100%

	&:hover
		& .eye
			height: 4px

			&__left
				background-image: url(../../assets/holaclosedeye_min.jpg)

			&__right
				background-image: url(../../assets/holaclosedeye_min.jpg)


.face-screen
	position: absolute
	top: 33%
	width: 100%
	height: 35%
	border: 1px solid grey
	background-color: #050510

	display: flex
	justify-content: center
	align-items: center

.eye
	position: absolute
	width: 90px
	height: 52px

	background-size: 100%
	background-repeat: no-repeat
	background-position: center

	animation: blink 3s infinite 1s

	@keyframes blink
		0%
			background-image: url(../../assets/holaeye_min.jpg)
		4%
			background-image: url(../../assets/holaclosedeye_min.jpg)
		6%
			background-image: url(../../assets/holaeye_min.jpg)
		8%
			background-image: url(../../assets/holaeye_min.jpg)
		12%
			background-image: url(../../assets/holaclosedeye_min.jpg)
		14%
			background-image: url(../../assets/holaeye_min.jpg)
		100%
			background-image: url(../../assets/holaeye_min.jpg)

	&__left
		left: 10px
		background-image: url(../../assets/holaeye_min.jpg)

	&__right
		right: 10px
		background-image: url(../../assets/holaeye_min.jpg)
		transform: scaleX(-1)

</style>
