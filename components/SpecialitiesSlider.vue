<template>
	<div class="specialities-body">
		<div @click="slidePrev()" class="slider-controller left-controller">
			<i class="fa fa-chevron-left"></i>
		</div>
		<slider class="slider" ref="sliderSpeciality" :options="options">
			<!-- slideritem wrapped package with the components you need -->
			<slideritem v-for="(item,index) in specialities" style="width:14%" :key="index">
				<category :img="item.img" :title="item.title" />
			</slideritem>
			<!-- Customizable loading -->
			<div slot="loading">loading...</div>
		</slider>
		<div @click="slideNext()" class="slider-controller right-controller">
			<i class="fa fa-chevron-right"></i>
		</div>
	</div>
</template>

<script>
import { slider, slideritem } from 'vue-concise-slider'
import {mapState} from 'vuex'
import Category from '@/components/Category'
export default {
	data () {
		return {
			//data list [array]
			range: [125,587],
			//Slider configuration [obj]
			options: {
				currentPage: 0,
				infinite: 7,
				slidesToScroll: 7,
				pagination: false,
			}
		}
	},
	methods: {
		slideNext () {
			this.$refs.sliderSpeciality.$emit('slideNext')
		},
		slidePrev () {
			this.$refs.sliderSpeciality.$emit('slidePre')
		}
	},
	computed: {
		...mapState({
			specialities: ({Speciality}) => Speciality.all
		})
	},
	components: {
		slider,
		slideritem,
		Category
	}
}
</script>

<style scoped lang="scss">
	.specialities-body{
		position: relative;
		transform: translateY(-15px);
		margin: 10px 15px;
		background-color: white;
		z-index: 10;
		display: flex;
		height: 200px;
		border-radius: 5px;
		overflow: hidden;
		border: 1px solid rgb(226, 226, 226);
		.slider{
			display: block;
		}
		.slider-controller{
			height: 100%;
			background: #f5f5f5;
			display: flex;
			align-items: center;
			padding: 1.2rem;
			font-size: 1.2rem;
			color: #00cae9;
			cursor: pointer;
		}
	}
</style>