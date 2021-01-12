<template>
	<base-card>
		<base-button @click="setSelected('storedResource')" :mode="storedResourceMode">	
			Stored Resources
		</base-button>
		<base-button @click="setSelected('addResource')" :mode="addResourceMode">	
			Add Resource
		</base-button>
		<ul v-if="this.currentSelected === 'storedResource'">
			<learning-resource
				v-for="res in storedResources"
				:key="res.id"
				:id="res.id"
				:title="res.title"
				:link="res.link"
				@delete-resource="deleteResource"
			>
			</learning-resource>
		</ul>
		<add-resource v-else
			@add-resource="addResource"
		>
		</add-resource>
	</base-card>
</template>

<script>
import LearningResource from './LearningResource.vue'; 
import AddResource from './AddResource.vue'; 

export default {
	components: {LearningResource, AddResource},

	data() {
		return {
			currentSelected: 'storedResource',
			storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org',
        },
      ]
		}
	},

	computed: {
		storedResourceMode() {
			return this.currentSelected === 'storedResource' ? '' : 'flat';
		},	
		addResourceMode() {
			return this.currentSelected === 'addResource' ? '' : 'flat';
		}	
	},

	methods: {

		setSelected(selected) {
			this.currentSelected = selected;
		},

		deleteResource(id) {
			const idx = this.storedResources.findIndex(res => res.id === id);	
			this.storedResources.splice(idx, 1);
		},	

		addResource(title, description, link) {
			const resource = {
				id: title,
				title,
				description,
				link
			}
			this.storedResources.push(resource);
			this.setSelected('storedResource');
		}
	}
}
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
