<template>
  <div class="photo">
    <img :src="imageUrl" :alt="alt" loading="lazy">
  </div>
</template>

<script>
export default {
  props: ['imageUrl', 'alt'],
}
</script>

<style scoped>
.photo {
  margin-bottom: 5px;
}

img {
  width: 100%;
  border-radius: 5px;
}
</style>