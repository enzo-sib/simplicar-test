<template>
  <div class="grid grid-cols-4 px-5">
    <div v-for="(thumbnail, index) in thumbnails" :key="index">
      <img v-if="indexVisible == index" class="border border-solid border-red-700 rounded-lg" :src="thumbnail">
      <img v-else class="border border-solid border-gray-400 rounded-lg" :src="thumbnail">
    </div>
  </div>
</template>

<script>
  export default {
    props: ['indexVisible', 'thumbnails']
  }
</script>

<style scoped>

</style>