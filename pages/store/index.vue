<template>
  <div class="pb-4">
    <div class="store-title d-flex align-items-center">
      <div class="container mx-auto py-8">
        <p class="py-8 uppercase SFDisplay-black text-white text-5xl m-0"> ¿Cuál va a ser tu próximo nissan?</p>
      </div>
    </div>
    <div class="container mx-auto">
      <div>
        <p> Hola soy una p </p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-8 gap-y-4">
        <CarCard v-for="car in cars" :key="car.id" :car="car"/>
      </div>
      <p class="legal py-8">*Los precios expuestos en este catalogo son expresados en dólares americanos. Los mismos incluyen IVA y podrán variar en función al modelo y/o versión elegida. El precio por unidad reflejado en este catálogo refiere a la unidad de versión más económica por cada modelo. RALITOR SA se reserva el derecho de modificar y actualizar los mismos en cualquier momento. Es responsabilidad del cliente confirmar al momento de su compra, el precio final que aparece en el catálogo. No se incluyen Gastos de empadronamiento ni cualquier tipo de costo municipal, así como tampoco gastos de traslados, fletes o seguro del vehículo. No incluye costos de instalación de accesorios.</p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        cars : [],
        carroceria: [],
        models: []
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
            let arrayCarroceria = []
            this.cars.forEach(element => {
              arrayCarroceria.push(element.specs.technical_details.body)
              this.models.push(element.model)
            })
            this.carroceria = arrayCarroceria.filter((item,index) => {
              return arrayCarroceria.indexOf(item) === index
            })
          })
      }
    },
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