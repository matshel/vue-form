<script>
	export default {
		data() {
			return {
				email: "",
				password: "",
				role: "default",
				terms: false,
				tempSkill: "",
				skills: [],
				passwordError: "",
			};
		},
		methods: {
			addSkill(e) {
				if (e.keyCode === 13 && this.tempSkill) {
					if (!this.skills.includes(this.tempSkill)) {
						this.skills.push(this.tempSkill);
					}
					this.tempSkill = "";
				}
			},
			deleteSkill(skill) {
				this.skills = this.skills.filter((item) => {
					return skill !== item;
				});
			},
			handleSubmit() {
				// validate password
				this.passwordError = this.password.length > 5 ? "" : "Password must be at least 6 characters";
				if (!this.passwordError) {
					console.log("email:", this.email);
					console.log("password:", this.password);
					console.log("role:", this.role);
					console.log("skills:", this.skills);
					console.log("terms accepted:", this.terms);
				}
			},
		},
	};
</script>

<template>
	<form @submit.prevent="handleSubmit">
		<label>Email:</label>
		<input type="email" required v-model="email" />

		<label>Password:</label>
		<input type="password" required v-model="password" />
		<div v-if="passwordError" class="password-error">{{ passwordError }}</div>

		<label>Role:</label>
		<select v-model="role">
			<option value="default">Select Role</option>
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>

		<label>Skills:</label>
		<input type="text" v-model="tempSkill" @keyup.alt="addSkill" placeholder="Alt + Enter to add your skill" />

		<div v-for="skill in skills" :key="skill" class="pill">
			<span @click="deleteSkill(skill)"> {{ skill }} </span>
		</div>

		<div class="terms">
			<input type="checkbox" required v-model="terms" />
			<label>Accept terms and conditions</label>
		</div>

		<div class="submit">
			<button>Create an account</button>
		</div>
	</form>

	<!-- check output -->
	<!-- <p>Email: {{ email }}</p>
	<p>Password: {{ password }}</p>
	<p>Role: {{ role }}</p>
	<p>Terms accepted: {{ terms }}</p> -->
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
	input,
	select {
		display: block;
		padding: 10px 6px;
		width: 100%;
		border: none;
		border-bottom: 1px solid #ddd;
		color: #555;
	}
	input[type="checkbox"] {
		display: inline-block;
		position: relative;
		top: 2px;
		width: 16px;
		margin: 0 10px 0 0;
	}
	.pill {
		display: inline-block;
		margin: 20px 10px 0 0;
		padding: 6px 12px;
		font-size: 12px;
		letter-spacing: 1px;
		font-weight: bold;
		color: #777;
		background-color: #eee;
		border-radius: 20px;
		cursor: pointer;
	}
	button {
		background-color: #0b6dff;
		border: none;
		padding: 10px 20px;
		margin-top: 20px;
		color: #fff;
		border-radius: 20px;
	}
	.submit {
		text-align: center;
	}
	.password-error {
		color: #ff0062;
		margin-top: 10px;
		font-size: 0.8rem;
		font-weight: bold;
	}
</style>
