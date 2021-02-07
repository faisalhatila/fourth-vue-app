<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"> </component>
  </keep-alive>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import StoredResources from './StoredResources';
import AddResource from './AddResource';

export default {
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The officcial Vue.js documentaion',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.com',
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId){
        // this.storedResources = this.storedResources.filter(res => res.id !== resId)
        // console.log(this.storedResources.length)
        const resIndex = this.storedResources.findIndex(res => res.id === resId)
        this.storedResources.splice(resIndex,1)
    }
  },
  components: { BaseButton, StoredResources, AddResource },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource:this.removeResource
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab !== 'stored-resources' && 'flat';
    },
    addResButtonMode() {
      return this.selectedTab !== 'add-resource' && 'flat';
    },
  },
};
</script>

<style lang="scss" scoped></style>
