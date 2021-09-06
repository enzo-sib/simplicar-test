<template>
  <div>
      <div class="content">
        <Nav />
        <Nuxt />
      </div>
      <Footer />
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
  .content{
    background-image: url(~/assets/img/background-index.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position-x: center;
    background-position-y: bottom;
    width: 100%;
    height: 810px;
  }
</style>
