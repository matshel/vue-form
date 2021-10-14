<script>
	import SignupForm from "./components/signupForm.vue";

	export default {
		name: "App",
		components: {
			SignupForm,
		},
	};
</script>

<template>
	<SignupForm />
</template>

<style>
	* {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
	body {
		background-color: #eee;
	}
</style>
