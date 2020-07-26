<template>
	<div class="sh-button primary" @click="toRoute()">
		<div class="sub-container">
			<div class="text">
				{{text}}
			</div>
			<div v-if="this.img" class="icon">
				<img :src="getImg()" :class="{'invert': invert}"/>
			</div>
		</div>
	</div>	
</template>

<script>
	export default {
		props: {
			text: {
				type: String
			},
			img: {
				default: false
			},
			invert: {
				type: Boolean, 
				default: false
			},
			to: {
				required: false
			}
		},
		methods: {
			getImg () {
				return this.img 
					? require('../assets/image/' + this.img)
					: ''
			},
			toRoute () {
				if (typeof this.to === 'object') {
					this.$router.push({name: this.to.name})
				} else if (typeof this.to === 'string') {
					this.$router.push({name: this.to})
				}
				this.$emit('click')
			}
		}
	}
</script>

<style scoped lang="scss">
	.sh-button{
		cursor: pointer;
		display: inline-block;
		border-radius: 15px;
		padding: 8px 25px;
		.sub-container{
			display: flex;
			align-items: center;
			.text{
				margin-bottom: 0;
				display: inline-block;
				color: white;
				font-size: 1rem;
				b{
					color: white
				}
			}
			.icon{
				display: inline-block;
				height: 1.8rem;
				display: inline-block;
				margin-left: 10px;
				img{
					height: 100%;
				}
			}
		}
		.invert{
			filter: invert(1)
		}
	}
</style>