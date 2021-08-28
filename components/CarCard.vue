<template>
  <div class="col-md-4">
    <NuxtLink to="/" class="text-decoration-none">
    <div class="card-container">
      <div class="row m-3">
        <img class="p-0" src="~/assets/img/car.jpg" />
        <p class="card-name my-2 SFDisplay-bold uppercase">VERSA</p>
        <div class="divider"></div>
        <div class="d-flex flex-row my-4 p-0">
          <div class="col-8 p-0 d-flex align-items-center">
            <p class="price-title uppercase SFDisplay-bold p-0 m-0">Precio desde</p>
          </div>
          <div class="col-4 p-0 ml-auto">
            <p class="price uppercase SFDisplay-bold p-0 m-0">US$ 15,990</p>
          </div>
        </div>
        <div class="divider"></div>
        <div class="col-12 p-0">
          <div class="card-details col-12 d-flex align-items-center uppercase SFDisplay-medium pt-3 pb-1">
            <div class="col-11">
              ver detalles de modelo
            </div>
            <i class="card-details-icon col-1 ri-arrow-right-line"></i>
          </div>
          <div class="col-12 mt-2">
            <p class="p-0 card-advise">Imágenes meramente ilustrativas no reportando la realidad exacta, pudiendo existir variaciones en la percepción.</p>
          </div>
        </div>
      </div>
    </div>
    </NuxtLink>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
  .card-container:hover{
    outline: 1px solid #e3e2e2;
    border-radius: 9px;
  }
  .card-name{
    font-size: 25px;
    color: #343434;
    text-align: center;
  }
  .divider{
    border-top: 1px solid #e3e2e2;
  }
  .price-title{
    color: #b6b6b6;
    font-size: 14px;
  }
  .price{
    color: #343434;
    font-size: 16px;
    text-align: right;
  }
  .card-details{
    color: #c3002f;
  }
  .card-details-icon{
    font-size: 115%;
  }
  .card-advise{
    color: #c1c1c1;
    font-size: 13px;
  }
</style>