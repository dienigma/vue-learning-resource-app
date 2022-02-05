<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['mode'],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #2ecc71;
  border: 1px solid #2ecc71;
  color: white;
  cursor: pointer;
  border-radius: 8px;
}

button:hover,
button:active {
  background-color: #27ae60;
  border-color: #27ae60;
}

.flat {
  background-color: transparent;
  color: #2ecc71;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #ecf0f1;
}
</style>
