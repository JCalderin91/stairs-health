<template>
	<v-row>
		<v-col :md="4" class="info-box">
			<h1>4</h1>
			<p>Anciallary services</p>
		</v-col>
		<v-col :md="4" class="info-box active">
			<h1>$ 500</h1>
			<p>Gross charge</p>
		</v-col>
		<v-col :md="4" class="info-box">
			<h1>$ 15</h1>
			<p>Apply Discount</p>
		</v-col>
		<v-col :md="12" align="center">
			<div class="my-3 mx-10">
				<v-text-field style="width: 250px" class="v-input--is-focused primary--text focused" rounded placeholder="Chooce you insurance" 
				outlined >
					<v-icon slot="append" color="primary">
							mdi-shield-check-outline
					</v-icon>
				</v-text-field>
			</div>	
			<br>
			<table class="table w-100">
				<thead>
					<tr>
						<th>Ancillary Services</th>
						<th>CPT/HCPS</th>
						<th>Charge</th>
					</tr>
				</thead>
				<tbody>
					<tr v-for="(item, key) in tabla_1" :key="key">
						<td>{{item.ac}}re</td>
						<td class="text-center">{{item.cpt}}</td>
						<td class="text-center">$ {{item.charge}}</td>
					</tr>
				</tbody>
			</table>

			<div class="separador"></div>

			<table class="table w-100">
				<thead>
					<tr>
						<th>Charges</th>
						<th>Price</th>
					</tr>
				</thead>
				<tbody>
					<tr v-for="(item, key) in tabla_2" :key="key">
						<td>{{item.charges}}</td>
						<td class="text-center">$ {{item.price}}</td>
					</tr>
				</tbody>
			</table>
		</v-col>
	</v-row>
</template>

<script>
	export default {
		data: () => ({
			tabla_1: [
				{
					ac: 'Primari diagnostic procedure',
					cpt: 'XXX',
					charge: '100'
				},{
					ac: 'anestesia',
					cpt: 'XXX',
					charge: '100'
				},{
					ac: 'Pathology',
					cpt: 'XXX',
					charge: '100'
				},{
					ac: 'Phisician services',
					cpt: 'XXX',
					charge: '100'
				}
			],
			tabla_2: [
				{
					charges: 'Discounted Cash Price',
					price: '100',
				},{
					charges: 'Minimum Negociate Charge',
					price: '100',
				},{
					charges: 'Maximum Negociate Charge',
					price: '100',
				}
			],

		})
	}
</script>

<style scoped lang="scss">

.info-box{
	text-align: center;
	h1{
		font-weight: 200 !important;
	}
	&.active{
		background: #00cae933;
		border-radius: 5px;
	}
}

.table{
	margin: 15px 5px;
	td{
		padding: 5px;
	}
}
.w-100{
	width:100%;
}

</style>