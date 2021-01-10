<template>
	<form @submit.prevent="addUser">
		<input type="text" ref="name" placeholder="name" />
		<input type="number" ref="age" placeholder="age" />
		<button>Add</button>
	</form>
</template>

<script>
	export default {
		emits: ['add-user'],
		data() {
			return {
				name: '',
				age: 0
			};
		},
		methods: {
			addUser() {
				const name = this.$refs.name.value;	
				const age = this.$refs.age.value;
				this.$emit('add-user', {name, age});
			}
		}	
	}
</script>

<style>
	input {
		display: block;
		margin: 1rem;
	}
</style>
