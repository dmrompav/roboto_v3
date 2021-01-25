<template lang="pug">
	nav.nav
		ul.ul
			li.li(v-for="content in buttonContents" :key="content.ind")
				button.button.cybr-btn.cybr-a
					| {{ content.title }}
					span.cybr-btn__glitch(aria-hidden) {{ content.title }}
			li.li
				button.button.cybr-btn(@click="abort")
					| Назад
					span.cybr-btn__glitch(aria-hidden) Назад
		
</template>

<script>
export default {
	name: 'PudubotNav',
	data() {
		return {
			buttonContents: [
				{
					ind: 11,
					title: 'Заголовок1',
				},
				{
					ind: 12,
					title: 'Заголовок2',
				},
				{
					ind: 13,
					title: 'Заголовок3',
				},
				{
					ind: 14,
					title: 'Заголовок4',
				},
			]
		}
	},
	methods: {
		abort() {
			this.$emit('abort')
		}
	}
}
</script>

<style  lang="sass" scoped>

</style>
