<template>
  <base-dialog v-if="isInputInvalid" title="Invalid Input" @close="confirmErr">
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>Please check all inputs.</p>
    </template>
    <template #actions>
      <base-button @click="confirmErr"> Close </base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="onAdd">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="title" />
      </div>
      <div class="form-control">
        <label for="description">Descrption</label>
        <textarea
          name="description"
          id="description"
          ref="description"
          rows="3"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="link" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  data() {
    return {
      isInputInvalid: false,
    };
  },
  methods: {
    onAdd() {
      const title = this.$refs.title.value;
      const description = this.$refs.description.value;
      const link = this.$refs.link.value;
      if (
        title.trim() === '' ||
        description.trim() === '' ||
        link.trim() === ''
      ) {
        this.isInputInvalid = true;
        return;
      }
      this.addResource(title, description, link);
    },
    confirmErr() {
      this.isInputInvalid = false;
    },
  },
};
</script>

<style scoped>
form {
  width: 100%;
}
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #2ecc71;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
  width: 100%;
}
</style>
