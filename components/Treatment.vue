<template>
	<v-card id="treatment" class="mb-5">
		<v-row>
			<v-col :md="3" class="pl-6">
				<v-img height="200px" gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.4)" src="@/assets/image/0.png">
				</v-img>
			</v-col>
			<v-col :md="4">
				<h2 class="title-clinic">Clinic Domenic</h2>
				<information />
			</v-col>
			<v-col :md="5" class="more-info py-0">
				<div class="treatment-text py-3">
					<h3>Details Treatment</h3>
					<table class="table-treatment-deatils">
						<tbody>
							<tr>
								<th>Speciality</th>
								<td>Cardiology</td>
							</tr>
							<tr>
								<th>Treatment</th>
								<td>By-Pass</td>
							</tr>
							<tr>
								<th>Proffesional</th>
								<td>Domenico La Morgia</td>
							</tr>
							<tr>
								<th>Date</th>
								<td>25 January, 2020</td>
							</tr>
							<tr>
								<th>Hour</th>
								<td>12:00 h</td>
							</tr>
						</tbody>
					</table>
				</div>
				<div class="treatment-options">
					<div class="treatment-options-item"><i class="fa fa-eye"></i></div>
					<div class="treatment-options-item"><i class="fa fa-times-circle"></i></div>
					<div class="treatment-options-item"><i class="fa fa-phone"></i></div>
					<div class="treatment-options-item"><i class="fa fa-info-circle"></i></div>
				</div>
			</v-col>
		</v-row>
	</v-card>
</template>

<script>
	import Information from '@/components/Information'
	export default {
		components: {Information}
	}
</script>

<style scoped lang="scss">
#treatment {
	box-shadow: none;
	border: 1px solid rgb(219, 219, 219);
	overflow: hidden;

	.title-clinic {
		font-weight: 100;
		font-size: 2rem;
	}

	.more-info {
		background-color: #f5f5f5;
		display: flex;
		justify-content: space-between;

		.treatment-options {
			background-color: white;
			height: 100%;
			display: flex;
			flex-direction: column;
			justify-content: space-between;

			.treatment-options-item {
				padding: .5rem 1.2rem;
				cursor: pointer;
				transition: all .3s ease-in-out;
				font-size: 1.3rem;

				&:hover {
					background-color: #ccc;
				}
			}
		}

	}

	.table-treatment-deatils {
		th {
			text-align: left;
			padding: 2px 15px 2px 2px;
		}
	}
}
</style>