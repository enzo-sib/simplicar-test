<template>
  <div v-show="indexVisible === index" class="carrusel-slide">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    props: ['indexVisible', 'index']
  }
</script>

<style scoped>

</style>