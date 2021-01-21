<template lang="pug">
	nav.nav
		ul.ul
			li.li(v-for="content in buttonContents" :key="content.ind")
				button.button.cybr-btn(@click="NavButClick(content.ind)")
					| {{ content.title }}
					span.cybr-btn__glitch(aria-hidden) {{ content.title }}

</template>

<script>
export default {
	name: 'ServiceNav',
	data() {
		return {
			buttonContents: [
				{
					ind: 11,
					title: 'Bella Bot',
				},
				{
					ind: 12,
					title: 'Hola Bot',
				},
				{
					ind: 13,
					title: 'Pudu Bot',
				},
				{
					ind: 14,
					title: 'Puductor',
				},
			]
		}
	},
	methods: {
		NavButClick(i) {
			this.$emit('ServiceNavButClick', i)
		}
	}
}
</script>

<style  lang="sass" scoped>
@import '../../assets/_glitch.sass'

.nav
	position: relative
	z-index: 1

.ul
	width: 300px
	overflow: hidden


.li
	width: 250px
	padding: 10px

.button

	&:hover
		color: #fff

</style>
