<template>
  <base-card>
    <base-button @click="setSelected('stored-resources')"
     :mode="storedResButtonMode">Stored Resources</base-button
    >
    <base-button @click="setSelected('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
  </base-card>
  <keep-alive>
  <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official VueJS documentation.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google Reference',
          description: 'The Google site searches reference.',
          link: 'https://google.com'
        }
      ]
    };
  },
  provide() {
      return {
          resources: this.storedResources,
          addResource: this.addResources,
          removeResource: this.removeResource
      }
  },
  methods: {
    setSelected(tab) {
      this.selectedTab = tab;
    },
    addResources(newResource) {
      this.storedResources.unshift(newResource)
      this.selectedTab = 'stored-resources'
    },
    removeResource(resourceId) {
      const resourceIndex = this.storedResources.find(resource => resource.id === resourceId)
      this.storedResources.splice(resourceIndex, 1);
    }
  },
  computed: {
      storedResButtonMode() {
          return this.selectedTab === 'stored-resources' ? null : 'flat'
      },
      addResButtonMode() {
          return this.selectedTab === 'add-resource' ? null : 'flat'
      }
  },
  components: {
    StoredResources,
    AddResource
  }
};
</script>
