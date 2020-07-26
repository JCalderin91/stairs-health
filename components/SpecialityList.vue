<template>
	<section>
		<transition name="fade" mode="out-in">
			<div v-if="!viewSpeciality" class="px-10">
				<v-text-field
					:label="`Specialities: ${specialitiesCount}`"
					outlined
					rounded
					append-icon="mdi-magnify"
					v-model="specialitySearch"
				></v-text-field>
			</div>
		</transition>
		<div>
			<div v-if="filterSpecialities.length === 0" class="text-center d-block">No matches found</div>
			<transition name="fade" mode="out-in">
				<speciality v-if="viewSpeciality" @back="viewSpeciality = false" :speciality="speciality" />
				<transition-group name="list" tag="div" v-else class="list-specialities">
					<div class="list-specialities-item" @click="selectSpeciality(speciality)" v-for="(speciality, key) in filterSpecialities" :key="key">
						<category  :active="speciality.title==='Cardiology'" :img="speciality.img" :title="speciality.title" />
					</div>
				</transition-group>
			</transition>
		</div>
	</section>
</template>

<script>
	import Category from '@/components/Category'
	import Speciality from '@/components/Speciality'

	import {mapState} from 'vuex'
	export default {
		components: {
			Category, Speciality
		},
		data: () => ({
			specialitySearch: '',
			speciality: {}, 
			viewSpeciality: false
		}),
		methods: {
			selectSpeciality (speciality) {
				this.speciality = speciality
				this.viewSpeciality = true
			}
		},
		computed:{
			...mapState({
				specialities: ({Speciality}) => Speciality.all
			}),
			filterSpecialities () {
				return this.specialitySearch.length === 0 
					? this.specialities
					: this.specialities.filter(category => category.title.toUpperCase().includes(this.specialitySearch.toUpperCase()))
			},
			specialitiesCount () {
				return this.filterSpecialities.length
			}
		}
	}
</script>

<style scoped lang="scss">
	.list-specialities{
		max-height: 500px;
		overflow	: auto;
		display: flex;
		flex-wrap: wrap;
		.list-specialities-item{
			width: 33.3%;
		}
	}
</style>