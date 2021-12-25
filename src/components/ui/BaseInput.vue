<template>
  <input
    type="text"
    placeholder="Try somthing..."
    v-model="searchText"
    @input="getSearchText"
  />
</template>

<script>
export default {
  name: 'BaseInput',
  emits: ['submit'],
  data() {
    return {
      searchText: '',
    };
  },
  methods: {
    getSearchText(evt) {
      const input = evt.target;

      let handle = input.dataset.handle;
      if (handle) {
        clearTimeout(handle);
      }

      handle = setTimeout(() => {
        if (this.searchText) {
          this.$emit('submit', this.searchText);
        }
      }, 1000);

      input.dataset.handle = handle;
    },
  },
};
</script>

<style scoped>
input {
  width: 100%;
  border: 1px solid #ccc;
  height: 30px;
  border-radius: 5px;
  padding: 0 0.5rem;
  font-size: 0.9rem;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

input:focus {
  outline: none;
}
</style>
