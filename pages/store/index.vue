<template>
  <div class="pb-4">
    <div class="store-title d-flex align-items-center">
      <div class="container mx-auto py-8">
        <p class="py-8 uppercase SFDisplay-black text-white text-2xl sm:text-5xl m-0 text-center md:text-left"> ¿Cuál va a ser tu próximo nissan?</p>
      </div>
    </div>
    <div class="container mx-auto" v-if="cars.length > 0">
      <div class="grid grid-cols-2 items-center mt-5 mb-2 uppercase text-sm">
        <p class="p-0 text-gray-600">{{carsToShow.length}} vehículos</p>
        <p @click="openCloseMobileFilter ()" class="text-right md:hidden text-red-600 text-lg">Filtros</p>
      </div>
      <Filtros :filters="filters" :carsToShow="carsToShow" @quitarFiltro="quitarFiltro" :mobileFilter="mobileFilter"/>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-8 gap-y-4">
        <CarCard v-for="car in carsToShow" :key="car.id" :car="car"/>
      </div>
      <p class="legal py-8">*Los precios expuestos en este catalogo son expresados en dólares americanos. Los mismos incluyen IVA y podrán variar en función al modelo y/o versión elegida. El precio por unidad reflejado en este catálogo refiere a la unidad de versión más económica por cada modelo. RALITOR SA se reserva el derecho de modificar y actualizar los mismos en cualquier momento. Es responsabilidad del cliente confirmar al momento de su compra, el precio final que aparece en el catálogo. No se incluyen Gastos de empadronamiento ni cualquier tipo de costo municipal, así como tampoco gastos de traslados, fletes o seguro del vehículo. No incluye costos de instalación de accesorios.</p>
    </div>
    <div class="container mx-auto py-40" v-else >
      <img class="mx-auto" src="~/assets/img/loading.gif" />
      <p class="text-center text-2xl mt-4">Por favor aguarde a que carguen los productos</p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        cars : [],
        carsToShow: [],
        carrocerias: [],
        models: [],
        filters: [],
        mobileFilter: false
      }
    },
    mounted() {
      this.getCars()
    },
    methods: {
      async getCars() {
        const url = 'https://4my1q6hsyo.api.quickmocker.com/products'
        await this.$axios.$get(url, {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer qwertyuiopasdfghjklzxcvbnm123456'
          }
        })
        .then(res => {
            this.cars = res.results
            this.carsToShow = res.results
            let arrayCarroceria = []
            this.cars.forEach(element => {
              arrayCarroceria.push(element.specs.technical_details.body)
              this.models.push(element.model)
            })
            this.carrocerias = arrayCarroceria.filter((item,index) => {
              return arrayCarroceria.indexOf(item) === index
            })
            this.makeFilters()
          })
      },
      makeFilters(){
        this.filters.push(
          {
            name: "carrocería",
            name_dialog: "carrocería del vehículo",
            select: this.carrocerias,
            values: this.carrocerias
          },
          {
            name: "modelo",
            name_dialog: "modelo del vehículo",
            select: this.models,
            values: this.models
          },
          {
            name: "precio",
            name_dialog: "rango de precio",
            select: [
              'Entre 10000 y 20000',
              'Entre 20000 y 30000',
              'Entre 30000 y 40000'
            ],
            values: [
              '10000-20000',
              '20000-30000',
              '30000-40000'
            ]
          }
        )
      },
      quitarFiltro(data){
        const { filtros } = data
        if(filtros.length > 0){
          let carsFilter = this.cars
          filtros.forEach(el => {
            const carsFiltered = this.filterCars(el, carsFilter)
            carsFilter = carsFiltered
          });
          this.carsToShow = carsFilter
        }else{
          this.carsToShow = this.cars
        }
      },
      filterCars(filtro, carsFilter){
        const { name , value } = filtro
        let carsToFilter = carsFilter.filter(item => {
          switch (name) {
            case "carrocería":
              return item.specs.technical_details.body == value
            case "modelo":
              return item.model == value
            case "precio":
              const parts = param.value.split("-");
              const carPrice = item.detail.price.amount
              return parts[0] < carPrice && parts[1] > carPrice
            default:
              break;
          }
        })
        return carsToFilter
      },
      openCloseMobileFilter () {
        this.mobileFilter = this.mobileFilter ? false : true
      }
    }
  }
</script>

<style scoped>
  .store-title{
    background-color: #ccc;
  }
  .legal{
    font-size: 14px;
    line-height: 17px;
    color: #c1c1c1;
  }
</style>