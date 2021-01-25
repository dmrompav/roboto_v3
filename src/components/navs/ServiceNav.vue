<template lang="pug">
	nav.nav(@mouseleave="MouseLeave")
		ul.ul
			li.li(v-for="content in buttonContents" :key="content.ind" @mouseenter="MouseEnter(content.ind)")
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
		},
		MouseEnter(i) {
			this.$emit('hovered', i)
		},
		MouseLeave() {
			this.$emit('nonhovered')
		}
	}
}
</script>

<style  lang="sass" scoped>

</style>
