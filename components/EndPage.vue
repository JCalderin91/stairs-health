<template>
	<div id="footer">		
		<footer class="primary">
			<v-container class="py-5">
				<v-row>
					<v-col :md="3">
						<ul class="list-group">
							<li class="list-item">How it Works</li>
							<li class="list-item">Explore Savings</li>
							<li class="list-item">Become a Menmber</li>
							<li class="list-item">For Providers</li>
							<li class="list-item">Contact Us</li>
						</ul>
					</v-col>
					<v-col :md="3">
						<ul class="list-group">
							<li class="list-item">
								<i class="fa fa-facebook"></i>
								<span>Facebook</span>
							</li>
							<li class="list-item">
								<i class="fa fa-twitter"></i>
								<span>Twitter</span>
							</li>
							<li class="list-item">
								<i class="fa fa-instagram"></i>
								<span>Instagram</span>
							</li>
						</ul>
					</v-col>
					<v-col :md="3">
						<h4>You are provider?</h4>
						<span class="d-block">Contact Us</span>
						<span class="d-block">Know our provider's Services</span>
					</v-col>
					<v-col :md="3">
						<h4>
							Get the Stairs Health App
						</h4>
						<img class="get-app-image" src="@/assets/image/google_play.png" alt="">
						<img class="get-app-image" src="@/assets/image/app_store.png" alt="">
					</v-col>
				</v-row>
			</v-container>
		</footer>
		<div class="end">
			<v-container>
				<div class="end-between">
					<div>
						&copy; 2020 Stairs Healthcare, Inc. All right reserved. 
						<span class="terms">Terms</span>
						<span class="privacy">Privacy</span>
					</div>	
					<div>
						&copy; Nativo Creative Team 2020
					</div>		
				</div>
			</v-container>
		</div>
	</div>
</template>

<style scoped lang="scss">
#footer{
	z-index: 2;
}
footer{
	color: white;
	.list-group{
		.list-item{
			list-style: none;
			i{
				width: 1.5rem;
			}
		}
	}
	.get-app-image{
		height: 3rem;
	}
}
.end{
	background: #0BBBEF;
	color: white;
	font-size: .8rem;
	.end-between{
		display: flex;
		justify-content: space-between;
		.terms,
		.privacy{
			margin: 0 15px; 
			opacity: 0.7;
		}
	}
}
</style>