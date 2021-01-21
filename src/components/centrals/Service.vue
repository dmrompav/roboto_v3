<template lang="pug">
	.logo
		h1.logo__caption(:class="isOpened") ufa robotics company
		img.logo__img(src="../../assets/logo.jpg")
</template>

<script>
export default {
	name: 'Service',
	props: {
		isOpened: String
	}
}
</script>

<style  lang="sass" scoped>
	.logo
		width: 100%
		height: 100%

		display: flex
		justify-content: center
		align-items: center

		&:hover>.logo__caption
			width: 140px
			opacity: 1

		&__caption
			position: relative

			overflow: hidden
			width: 0px
			opacity: 0
			
			color: #ffffff
			font-size: 24px
			text-transform: uppercase
			text-align: left

			transition: width 0.2s, opacity 0.2s

				
			&::before,&::after
				color: white
				content: "Ufa Robotics Company"
				text-transform: uppercase
				position: absolute
				width: 100%
				height: 100%
				background: black
				overflow: hidden
				top: 0

			&::before
				left: 3px
				text-shadow: -2px 0 red
				animation-name: glitch-animation-1
				animation-duration: 5s
				animation-timing-function: linear
				animation-delay: 0s
				animation-iteration-count: infinite
				animation-direction: reverse-alternate
				
			&::after
				left: -3px
				text-shadow: -2px 0 #00bbdd
				animation-name: glitch-animation-2
				animation-duration: 3s
				animation-timing-function: linear
				animation-delay: 0s
				animation-iteration-count: infinite
				animation-direction: reverse-alternate

			@keyframes glitch-animation-1
				$steps: 20
				@for $i from 0 through $steps 
					#{percentage($i*(1/$steps))} 
						clip: rect(random(150)+px, 140px, random(150)+px, 0px)
					
			@keyframes glitch-animation-2
				$steps: 20
				@for $i from 0 through $steps 
					#{percentage($i*(1/$steps))} 
						clip: rect(random(150)+px, 140px, random(150)+px, 0px)

			&.opened
				width: 140px
				opacity: 1

		&__img
			width: auto
			height: 150px
			
			

</style>
