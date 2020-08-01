<template>
	<section>
		<div>
			<v-text-field
				:label="`Services: ${filterServices.length}`"
				outlined
				rounded
				append-icon="mdi-magnify"
				v-model="serviceSearch"
			></v-text-field>
		</div>
		<div>
			<div class="list-services">
				<table class="w-100">
					<transition-group name="list" tag="tbody" key="table-services">
						<tr v-for="(service, key) in filterServices" :key="key">
							<td>{{service}}</td>
							<td class="text-right">100</td>
						</tr>
					</transition-group>
				</table>
				<transition name="fade" mode="out-in">
					<div v-if="filterServices.length===0" :md="12"  class="text-center d-block">No matches found</div>
				</transition>
			</div>
		</div>
	</section>
</template>

<script>
	export default {
		data: () => ({
			serviceSearch: '',
			services: [
				'New patient consult',
				'Follow up evaluation',
				'Electrocardiogram',
				'Echosonogram',
				'Nuclear Stress Test',
				'Pace maker check',
				'Plain Tredmill',
				'Cardiac PET',
				'Holter monitor'
			],
		}),
		computed: {
			filterServices () {
				return this.serviceSearch.length === 0 
					? this.services
					: this.services.filter(service => service.toUpperCase().includes(this.serviceSearch.toUpperCase())) 
			}
		}
	}
</script>

