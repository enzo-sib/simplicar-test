<template>
  <li class="list-item uppercase">
    <NuxtLink :to="link.src" class="list-item-link text-decoration-none" v-text="link.name"></NuxtLink>
  </li>
</template>

<script>
  export default {
    props: ["link"]
  }
</script>

<style scoped>
.list-item{
  font-size: .875rem;
  font-weight: 700;
  letter-spacing: .2px;
  z-index: 1000;
  padding-right: .5rem;
}
.list-item-link{
  color: #343434;
}
</style>