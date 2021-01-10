<template>
	<user-data @add-user="addUser"></user-data>
	<ul>
		<active-user v-for="user in users"
			:name="user.name"
			:age="user.age"
			:key="user.name"
		>
		</active-user>
	</ul>
</template>

<script>
	import ActiveUser from './components/ActiveUser.vue'
	import UserData from './components/UserData.vue'

	export default {

		components: {
			ActiveUser,
			UserData
		},

		data() {
			return {
				users: [
					{name:"name1", age:"10"},
					{name:"name2", age:"20"}
				]
			};
		},

		methods: {
			addUser(user) {
				this.users.push(user);
			}
		}
	}
</script>

<style>
	ul {
		list-style: none;
	}
</style>
