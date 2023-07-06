<template>
  <base-card>
    <base-button
        @click="seSelectedTab('stored-resources')"
        :mode="storedResButtonMode"
    >
      Stored Resources
    </base-button>

    <base-button
        @click="seSelectedTab('add-resource')"
        :mode="addResButtonMode"
    >
      Add Resources
    </base-button>
  </base-card>

  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";
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
            description: 'Learn to Google',
            link: 'https://google.org',
          },
        ],
      };
    },

    provide() {
      return {
        resources: this.storedResources,
      };
    },

    computed: {
      storedResButtonMode() {
        return this.selectedTab === 'stored-resources' ? null : 'flat';
      },

      addResButtonMode() {
        return this.selectedTab === 'add-resource' ? null : 'flat';
      },
    },

    methods: {
      seSelectedTab(tab) {
        this.selectedTab = tab;
      }
    }
  };
</script>