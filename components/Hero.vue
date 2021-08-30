<template>
  <div class="container mx-auto h-96">
    <div class="row mt-24">
      <div class="col-md-7">
          <div class="max-w-screen-sm">
            <p class="title uppercase mb-0 text-6xl SFDisplay-black">Ahora es online</p>
            <p class="descripcion SFDisplay-light">
              Con Nissan Store, podés acceder a tu nuevo 0km con todos los servicios asociados desde la comodidad de tu sofá. Probanos! 
            </p>
            <NuxtLink to="/store" class="button text-white flex flex-row justify-center items-center SFDisplay-medium 
            bg-red-700 font-medium h-14 w-80 rounded-lg mt-12 text-left">
              INGRESAR A NISSAN STORE
              <i class="ri-arrow-right-line"></i>             
            </NuxtLink>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
  .title {
    color: #c3002f;
  }
  .descripcion {
    font-size: 25px;
  }
  .button {
    background-color: #c3002f;
  }
</style>