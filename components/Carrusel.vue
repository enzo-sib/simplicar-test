<template>
  <div class="carrusel">
    <slot></slot>
    <i @click="prev" class="prev icon ri-arrow-left-s-line"></i> 
    <i @click="next" class="next icon ri-arrow-right-s-line"></i> 
  </div>
</template>

<script>
  export default {
    methods: {
      prev () {
        this.$emit('prev')
      },
      next () {
        this.$emit('next')
      }
    }
  }
</script>

<style scoped>
.carrusel{
  position: relative;
  max-width: 100%;
  overflow: hidden;
}
.icon{
  position: absolute;
  top: calc(50% - 20px);
  border: none;
  color: black;
  font-size: 50px;
}
.icon:hover{
  cursor: pointer;
}
.prev{
  left: 0;
}
.next{
  right: 0;
}
</style>