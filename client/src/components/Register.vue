<template>
	<div>
		<h1>Register</h1>

		<label>
			<input type="email" name="email" v-model="email" placeholder="email"/>
		</label>
		<br>
		<label>
			<input type="password" name="password" v-model="password" placeholder="password"/>
		</label>
		<br>
		<button @click="register">Complete Registration</button>
	</div>
</template>

<script>
	import AuthenticationService from '@/services/AuthenticationService'
	export default {
		name: 'Register',
		data () {
			return {
				email: '',
				password: ''
			}
		},
		watch: {
			email (value) {
				console.log(`Email has changed`, value)
			}
		},
		methods: {
			async register () {
				const response = await AuthenticationService.register({
					email: this.email,
					password: this.password
				});
				console.log(response)
			}
		},
		mounted() {
			setTimeout(() => {
				this.email = 'hello world'
			}, 2000)
		}
	}
</script>

<style scoped>

</style>
