<template>
	<div class="pa-10">
		<!-- <h2 class="text-center py-4">Log In</h2> -->
		<div class="optional-logins mb-10 mt-3">
			<a href="">
				<i class="fa fa-google"></i>
			</a>
			<a href="">
				<i class="fa fa-facebook"></i>
			</a>
			<a href="">
				<i class="fa fa-apple"></i>
			</a>
		</div>
		<div class="sub-title">
			<p class="sub-title-text">Log In auth</p>
		</div>
		<div class="form">
			<v-text-field label="Email Adress" outlined hide-details prepend-inner-icon="mdi-mail" class="mb-3"
				v-model="credentials.mail"></v-text-field>
			<v-text-field label="Password" outlined hide-details prepend-inner-icon="mdi-lock" v-model="credentials.password">
			</v-text-field>
			<v-checkbox v-model="credentials.checkbox" label="Remember me"></v-checkbox>
			<div class="d-flex justify-center">
				<sh-button text="Log In" />
			</div>
		</div>
	</div>
</template>

<script>
	import ShButton from '@/components/ShButton'
	export default {
		components: {
			ShButton
		},
		data: () => ({
			credentials: {}
		})
	}
</script>

<style scoped lang="scss">
	.main-title {
		text-align: center;
	}

	.optional-logins {
		text-align: center;

		a {
			padding: 3px 5px;
			margin: 0 10px;
			font-size: 1.5rem;
		}
	}

	.sub-title {
		border-top: 2px solid #f5f5f5;
		margin-top: .5rem;
		text-align: center;

		.sub-title-text {
			font-size: .8rem;
			transform: translateY(-.9rem);
			background-color: white;
			display: inline-block;
			padding: 0 .4rem;

		}
	}

	.optional-logins {
		a {
			transition: color .3s ease-in-out;

			&:hover {
				color: #444;
			}
		}
	}
</style>