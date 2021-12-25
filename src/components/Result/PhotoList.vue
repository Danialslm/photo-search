<template>
  <div class="wrapper">
    <div class="photos">
      <PhotoItem
        v-for="photo in photos"
        :key="photo.id"
        :alt="photo.alt_description"
        :image-url="photo.urls.thumb"
      />
    </div>
  </div>
</template>

<script>
import PhotoItem from './PhotoItem.vue';

export default {
  components: { PhotoItem },
  props: ['photos'],
};
</script>

<style scoped>
.wrapper {
  height: 600px;
  overflow-y: auto;
}

.photos {
  column-count: 3;
}

@media screen and (min-width: 576px) {
  .photos {
    column-count: 4;
  }
}
</style>
