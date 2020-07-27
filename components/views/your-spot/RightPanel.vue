<template>
	<div class="mx-10">
		<v-date-picker  header-color="#e6e6e6" full-width v-model="date"></v-date-picker>
		<div class="appointment">
			<div class="title">Avaliable appointments</div>
			<div v-for="appointment in appointments" :key="appointment.id" class="appointment-list">
				<div class="appointment-list-item" :class="{'booked': appointment.status === 'booked'}">
					<div class="sub-item hour">{{appointment.hour}}</div>
					<div class="sub-item status">
						{{appointment.status}}
					</div>
				</div>
			</div>
		</div>
		<div @click="toShedule()" class="schedule">Schedule</div> 
	</div>
</template>

<script>
	export default {
		data: () => ({
			date: new Date().toISOString().substr(0, 10),
			appointments: [
				{
					id: 1,
					hour: '09:00 h',
					status: 'active'
				},
				{
					id: 2,
					hour: '10:00 h',
					status: 'booked'
				},
				{
					id: 3,
					hour: '11:00 h',
					status: 'booked'
				},
				{
					id: 4,
					hour: '12:00 h',
					status: 'active'
				},
				{
					id: 5,
					hour: '13:00 h',
					status: 'active'
				}
			]
		}),
		methods: {
			toShedule () {
				this.$router.push({name:'treatment'})
			}
		}
	}
</script>

<style scoped lang="scss">
	.appointment {
		margin-top: 1rem;

		.title {
			text-align: center;
			background-color: #eee;
			padding: .5rem 0;
		}

		.appointment-list {
			.appointment-list-item {
				display: flex;
				margin: 2px 0;
				padding: .3rem 0;
				font-size: 1.2rem;
				transition: all .2s ease-in-out;

				.sub-item {
					width: 50%;
					text-align: center;

					&.status {
						color: transparent;
					}
				}

				&:hover:not(.booked) {
					cursor: pointer;
					background-color: #00cae9;
					color: white;
				}

				&.booked {
					background-color: #eee;

					.sub-item {
						color: #999;
					}
				}
			}
		}
	}

	.schedule {
		margin-top: 1rem;
		background-color: #00cae9;
		text-align: center;
		padding: .5rem;
		font-size: 1.3rem;
		color: white;
		cursor: pointer;
	}
</style>