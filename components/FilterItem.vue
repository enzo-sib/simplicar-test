<template>
  <div class="flex flex-row items-center uppercase text-xs border border-gray-200 rounded-lg px-1 py-1 mr-3">
    <p class="text-black">{{appliedFilter.name}}: {{appliedFilter.value}}</p>
    <i class="ri-close-line cursor-pointer text-base ml-2 text-red-900 p-0" @click="quitarFiltro()"></i> 
  </div>
</template>

<script>
  export default {
    props: ['appliedFilter', 'index'],
    methods: {
      quitarFiltro() {
        const data = { index : this.index, ref : this.appliedFilter.ref }
        this.$emit('quitarFiltro', data)
      }
    }
  }
</script>

<style scoped>

</style>