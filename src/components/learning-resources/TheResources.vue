<template>
  <base-card>
    <div>
      <base-button @click="setTab('stored-resources')" :mode="storedResBtnMode">
        Stored Resources
      </base-button>
      <base-button :mode="addResBtnMode" @click="setTab('add-resource')">
        Add Resource
      </base-button>
    </div>
  </base-card>
  <keep-alive>
    <component :is="current"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResources, AddResource },
  computed: {
    storedResBtnMode() {
      return this.current === 'stored-resources' ? 'flat' : null;
    },
    addResBtnMode() {
      return this.current === 'add-resource' ? 'flat' : null;
    },
  },

  data() {
    return {
      current: 'stored-resources',
      storedResources: [
        {
          id: 'official guide',
          title: 'Official Guide',
          description: 'The Official vue js docs',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You know how to google',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      storedResources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  methods: {
    setTab(item) {
      this.current = item;
    },
    addResource(title, description, link) {
      const newResource = {
        id: new Date().toString(),
        title,
        description,
        link,
      };
      this.storedResources.unshift(newResource);
      this.current = 'stored-resources';
    },
    removeResource(id) {
      const resIndex = this.storedResources.findIndex((res) => res.id === id);
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>

<style scoped>
div {
  display: flex;
  gap: 16px;
}
</style>
