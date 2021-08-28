<template>
  <div class="container index">
    <div class="row wrapper">
      <div class="col-md-7">
          <div class="text-container">
            <p class="uppercase title SFDisplay-black">Ahora es online</p>
            <p class="descripcion SFDisplay-light">
              Con Nissan Store, podés acceder a tu nuevo 0km con todos los servicios asociados desde la comodidad de tu sofá. Probanos! 
            </p>
            <button class="button d-flex flex-row justify-content-center align-items-center SFDisplay-medium">
              INGRESAR A NISSAN STORE
              <i class="ri-arrow-right-line"></i>             
            </button>
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
  .index{
    height: 595px;
  }
  .text-container {
    max-width: 625px;
  }
  .wrapper{
    margin-top: 115px;
  }
  .title {
    color: #c3002f;
    font-size: 61px;
    line-height: 61px;
    margin-bottom: 0 !important;
  }
  .descripcion {
    font-size: 25px;
  }
  .button {
    color: white;
    background-color: #c3002f;
    font-weight: 500;
    height: 60px;
    width: 350px;
    border-radius: 10px;
    border: none;
    margin-top: 53px;
    text-align: left;
  }
</style>