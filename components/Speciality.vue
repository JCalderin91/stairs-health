<template>
	<div class="py-3">
		<a href="" class="back-arrow" @click.prevent="back()">
			<i class="fa fa-arrow-left"></i> Back
		</a>
		<h2 class="text-center">{{speciality.title}}</h2>
		<speciality-icon noHover :img="speciality.img" noText />
		<service-list class="px-10" />
	</div>
</template>

<script>
	import SpecialityIcon from '@/components/Category'
	import ServiceList from '@/components/ServiceList'

	export default {
		components: {
			SpecialityIcon, ServiceList
		},
		props: {
			speciality: {
				type: Object,
				requires: true
			}
		},
		methods: {
			back () {
				this.$emit('back')
			}
		}
	}
</script>

<style scoped lang="scss">
	.back-arrow{
		position: absolute;
		padding: .3rem 1rem; 
		text-decoration: none;
	}
</style>