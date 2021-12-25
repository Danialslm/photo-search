<template>
  <div class="container">
    <TheSearchForm />
  </div>
</template>

<script>
import TheSearchForm from '@/components/TheSearchForm.vue';

export default {
  components: { TheSearchForm },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  min-height: 100vh;
  background-color: #f4f4f4;
}

.container {
  max-width: 500px;
  margin: 0 auto;
  padding: 0 1rem;
}
</style>
