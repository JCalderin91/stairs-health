<template>
	<div class="my-6">
		<info />
		<treatment />
		<v-container>
			<v-row>
				<v-col :md="6">
					<details-clinic />
				</v-col>
				<v-col :md="6">
					<right-panel />
				</v-col>
			</v-row>
		</v-container>
	</div>
</template>

<script>
	import Info from '@/components/InfoClinic'
	import Treatment from './Treatment'
	import DetailsClinic from '@/components/DetailsClinic'
	import RightPanel from './RightPanel'

	export default {
		components: {
			Info, Treatment, DetailsClinic, RightPanel
		}
	}
</script>