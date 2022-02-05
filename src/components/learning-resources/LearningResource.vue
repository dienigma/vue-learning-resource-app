<template>
  <li>
    <base-card>
      <div>
        <header>
          <h3>{{ title }}</h3>
          <base-button @click="removeItem(itemId)" mode="flat"
            >Delete</base-button
          >
        </header>
      </div>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resource</a>
      </nav></base-card
    >
  </li>
</template>

<script>
export default {
  props: ['title', 'description', 'link', 'itemId'],
  inject: ['removeResource'],
  methods: {
    removeItem(id) {
      this.removeResource(id);
    },
  },
};
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #2ecc71;
}

a:hover,
a:active {
  color: #2ecc71;
}
</style>
