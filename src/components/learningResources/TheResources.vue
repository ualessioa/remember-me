<template>
  <base-card>
    <base-button @click="setTab('stored-resources')" :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="setTab('add-resource')" :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You need to know how to google stuff!',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
    };
  },
  methods: {
    setTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, desc, link) {
      this.storedResources.unshift({
        id: new Date().toISOString(),
        title: title,
        description: desc,
        link: link,
      });
      this.selectedTab = 'stored-resources';
    },
  },
  props: ['resources'],
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? '' : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? '' : 'flat';
    },
  },
};
</script>
