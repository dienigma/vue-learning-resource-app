<template>
  <div>
    <header>
      <h2>{{ title }}</h2>
    </header>
  </div>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
div {
  width: 100%;
  background-color: #2ecc71;
}
header {
  max-width: 40rem;
  margin: 0 auto;
}
h2 {
  font-size: 48px;
  font-weight: bolder;
  margin-top: 0;
  margin-bottom: 24px;
  color: white;
  padding: 24px 0;
}
</style>
