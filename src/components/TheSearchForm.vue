<template>
  <div class="search-form">
    <h3>Photo Search 📷</h3>
    <BaseInput @submit="doSearch" />
  </div>
  <PhotoList :photos="result" ref="photoList" />
</template>
<script>
import { createApi } from 'unsplash-js';

import BaseInput from '@/components/ui/BaseInput';
import PhotoList from '@/components/Result/PhotoList.vue';

const unsplash = new createApi({
  accessKey: 'your unsplash access token',
});

export default {
  name: 'TheSearchForm',
  components: { BaseInput, PhotoList },
  data() {
    return {
      result: [],
      currentPage: 1,
      query: '',
    };
  },
  methods: {
    async doSearch(searchText) {
      this.result = [];

      const result = await unsplash.search.getPhotos({
        query: searchText,
        perPage: 20,
      });

      if (result.status === 200) {
        this.result = result.response.results;

        this.currentPage++;
        this.query = searchText;
      }
    },

    async loadMore() {
      const result = await unsplash.search.getPhotos({
        query: this.query,
        perPage: 10,
        page: this.currentPage,
      });

      if (result.status === 200) {
        result.response.results.forEach((item) => {
          this.result.push(item);
        });

        this.currentPage++;
      }
    },
  },
  mounted() {
    const listElm = this.$refs.photoList.$el;
    listElm.addEventListener('scroll', () => {
      if (listElm.scrollTop + listElm.clientHeight >= listElm.scrollHeight) {
        this.loadMore();
      }
    });
  },
};
</script>

<style scoped>
.search-form {
  width: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 1rem;
  flex-direction: column;
}

h3 {
  color: #333;
  margin-bottom: 1rem;
  text-align: center;
}
</style>
