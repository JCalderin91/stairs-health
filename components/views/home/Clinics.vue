<template>
	<v-container>
		<v-row wrap>
			<v-col :md="4" v-for="i in 6" :key="i">
				<router-link tag="div" :to="{name:'clinic'}">
					<card  />
				</router-link>
			</v-col>
		</v-row>
		<div class="my-3 primary more" @click="$router.push({name:'clinics'})">
			MORE OFFERTS
		</div>
	</v-container>
</template>

<script>
import Card from '@/components/Card'
export default {
	components: {Card}
}
</script>

<style scoped lang="scss">
.more{
	text-align: center;
	border-radius: 5px;
	color: white;
	padding: 15px 0;
	cursor: pointer;
	font-weight: bold;
}
</style>