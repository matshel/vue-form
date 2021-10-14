<script>
	export default {
		data() {
			return {
				email: "",
				password: "",
			};
		},
	};
</script>

<template>
	<form>
		<label>Email:</label>
		<input type="email" required v-model="email" />

		<label>Password:</label>
		<input type="password" required v-model="password" />
	</form>
	<p>Email: {{ email }}</p>
	<p>Password: {{ password }}</p>
</template>

<style>
	form {
		max-width: 420px;
		margin: 30px auto;
		padding: 40px;
		background-color: #fff;
		text-align: left;
		border-radius: 10px;
	}
	label {
		display: inline-block;
		color: #aaa;
		margin: 25px 0 15px;
		font-size: 0.6rem;
		text-transform: uppercase;
		letter-spacing: 1px;
		font-weight: bold;
	}
	input {
		display: block;
		padding: 10px 6px;
		width: 100%;
		border: none;
		border-bottom: 1px solid #ddd;
		color: #555;
	}
</style>
