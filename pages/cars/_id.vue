<template>
  <div class="pb-4">
    <div class="cars-title flex items-center">
      <div class="list flex flex-row py-4 px-5 uppercase">
        <NuxtLink to="/store" class="list-link list-font flex flex-row text-decoration-none">
          <i class="ri-arrow-left-line pr-2"></i> 
          <p class="SFDisplay-bold">Volver a la tienda</p>
        </NuxtLink>
        <p class="list-slash list-font SFDisplay-black">/</p>
        <p class="list-link list-font SFDisplay-medium" v-text="car.model"></p>
        <p class="list-slash list-font SFDisplay-black">/</p>
        <p class="list-mail list-font SFDisplay-medium">enviar cotización por mail</p>
      </div>
      <div class="row">
        <div class="col-6">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        car: []
      }
    },
    mounted() {
      this.getCar()
    },
    methods: {
      async getCar(){
        const id = this.$route.params.id
        const url = `https://4my1q6hsyo.api.quickmocker.com/product/${id}`
        await this.$axios.$get(url, {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer qwertyuiopasdfghjklzxcvbnm123456'
          }
        })
          .then(res => {
            this.car = res
          })
      }
    },
    delimiters: ["[[", "]]"]
  }
</script>

<style scoped>
  .cars-title{
    background-color: #ccc;
  }
  .list-font{
    font-size: .9rem;
    font-weight: 500;
    letter-spacing: .2px;
  }
  .list-link{
    color: #c3002f;
  }
  .list-slash{
    color: rgb(143, 143, 143);
    padding-left: 1rem;
    padding-right: 1rem;
  }
  .list p{
    margin: 0 !important;
  }
</style>