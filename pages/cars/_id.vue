<template>
  <div class="pb-4">
    <div class="cars-title flex items-center">
      <div class="list flex flex-row py-4 uppercase container mx-auto">
        <NuxtLink to="/store" class="list-link list-font flex flex-row text-decoration-none">
          <i class="ri-arrow-left-line pr-2"></i> 
          <p class="SFDisplay-bold">Volver a la tienda</p>
        </NuxtLink>
        <p class="list-slash list-font SFDisplay-black">/</p>
        <p class="list-link list-font SFDisplay-medium" v-text="car.model"></p>
        <p class="list-slash list-font SFDisplay-black">/</p>
        <p class="list-mail list-font SFDisplay-medium">enviar cotización por mail</p>
      </div>
    </div>
    <div v-if="car" class="container mx-auto grid grid-cols-1 lg:grid-cols-2 my-3">
      <div class="px-0 sm:px-7">
        <Carrusel @prev="prev()" @next="next()">
          <CarruselSlide v-for="(img, index) in imgs" 
                        :key="index" 
                        :index="index" 
                        :indexVisible="indexVisible"
                        >
            <img class="mx-auto" :src="img" />
          </CarruselSlide>
        </Carrusel>
        <CarruselThumbnail :indexVisible="indexVisible" :thumbnails="thumbnails" />
        <div class="my-3 divider"></div>
        <div class="grid grid-cols-2 text-gray-600 text-sm gap-y-4">
          <p><i class="ri-vuejs-fill"></i>{{caracteristicas.engine}}</p>
          <p><i class="ri-file-list-3-line"></i>{{caracteristicas.warranty}}</p>
          <p><i class="ri-git-branch-fill"></i>{{caracteristicas.gas_type}}</p>
          <p><i class="ri-car-line"></i> {{caracteristicas.body}}</p> 
        </div>
        <div class="my-3 divider"></div>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-2 text-decoration-none list-link uppercase text-sm">
          <NuxtLink to="/">ver todas las caracteristicas</NuxtLink>
          <NuxtLink to="/">ver galeria de imagenes</NuxtLink>
        </div>
      </div>
      <div class="text-left mt-5 md:mt-0">
        <p class="text-3xl text-black SFDisplay-medium uppercase">Ingresa tus datos</p>
        <p class="text-sm text-gray-500 mt-1 mb-5">Por favor completá el siguiente formulario para que uno de nuestro asesores se puede comunicar contigo</p>
        <form>
          <input type="text" class="border rounded-lg border-gray-400 px-7 py-3 w-full max-w-full mb-3" v-for="input in inputs" :key="input" :placeholder="input">
          <input type="submit" class="border rounded-lg bg-red-700 text-white px-7 py-3 w-full max-w-full mb-3 uppercase" value="enviarme la cotizacion por mail">
        </form>
      </div>
    </div>
    <div v-else class="container mx-auto py-40">
      <img class="mx-auto" src="~/assets/img/loading.gif" />
      <p class="text-center text-2xl mt-4">Por favor aguarde a que cargue el producto</p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        car: false,
        inputs: ['NOMBRE Y APELLIDO', 'CORREO ELECTRONICO', 'TELEFONO'],
        imgs: [],
        thumbnails: [],
        caracteristicas: [],
        indexVisible: 0
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
            this.caracteristicas = res.detail.characteristics
            const { gallery } = res
            gallery.forEach( n => {
              this.imgs.push(`https://s3.sa-east-1.amazonaws.com/simplimotos-stg.com/${n.large}`)
              this.thumbnails.push(`https://s3.sa-east-1.amazonaws.com/simplimotos-stg.com/${n.thumbnail}`)
            })
          })
      },
      prev(){
        if(this.indexVisible > 0) this.indexVisible--
      },
      next () {
        if(this.indexVisible < this.imgs.length - 1 ) this.indexVisible++
      }
    },
    delimiters: ["[[", "]]"]
  }
</script>

<style scoped>
  .divider{
    border-top: 1px solid #e3e2e2;
  }
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