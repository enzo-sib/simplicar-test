<template>
  <div class="mb-5">
    <div class="grid grid-cols-2">
      <div class="hidden md:flex flex-row items-center">
        <StoreFilter v-for="(filter, index) in filters" 
                    :ref="'filtro-'+ index" 
                    :referencia="'filtro-'+ index"
                    :key="filter.name" 
                    :filter="filter" 
                    @filtroStore="filterCars" 
                    />
      </div>
    </div>
    <div v-if="appliedFilters.length > 0" class="mt-2 flex flex-row items-center">
      <FilterItem v-for="(filter, index) in appliedFilters" :key="filter.name" :index="index" :appliedFilter="filter" 
        @quitarFiltro="quitarFiltro"/> 
      <p class="text-red-600 text-sm uppercase SFDisplay-bold" @click="borrarTodosFiltros()">borrar todo</p>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['filters','carsToShow'],
    data() {
      return {
        appliedFilters: [],
        ordenSelected: false,
        ordenarDialog: false,
        carsToFilter: this.carsToShow
      }
    },
    methods : {
      filterCars(param){
        const { value, name, ref } = param
        this.carsToFilter = this.carsToShow.filter(item => {
          switch (name) {
            case "carrocería":
              return item.specs.technical_details.body == value
            case "modelo":
              return item.model == value
            case "precio":
              const parts = value.split("-");
              const carPrice = item.detail.price.amount
              return parts[0] < carPrice && parts[1] > carPrice
            default:
              break;
          }
        })
        this.appliedFilters.push({ name, value, ref  })
        this.$parent.carsToShow = this.carsToFilter
      },
      abrirOrdenarDialog(){
        this.ordenarDialog = this.ordenarDialog ? false : true
      },
      quitarFiltro(param){
        const { ref, index } = param
        this.appliedFilters.splice(index , 1);
        const item = this.$refs[ref][0]
        item.filterPicked = false
        item.filterSelected = ""
        const data = { filtros : this.appliedFilters }
        this.$emit('quitarFiltro', data)
      },
      borrarTodosFiltros(){
        this.$parent.carsToShow = this.$parent.cars
        this.appliedFilters.forEach((el, index) => {
          const filtro = `filtro-${index}`
          const ref = this.$refs[filtro][0]
          ref.filterPicked = false
          ref.filterSelected = ""
        })
        this.appliedFilters = []
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>