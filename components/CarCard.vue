<template>
  <NuxtLink :to="redirect" class="text-decoration-none">
    <div class="card-container">
      <div class="m-3">
        <img class="max-w-full mx-auto p-0" :src="img" />
        <p class="card-name my-2 SFDisplay-bold uppercase" v-text="car.model"></p>
        <div class="divider"></div>
        <div class="flex flex-row my-4 p-0">
          <div class="p-0 flex items-center">
            <p class="price-title uppercase SFDisplay-bold p-0 m-0">Precio desde</p>
          </div>
          <div class="p-0 ml-auto">
            <p class="price uppercase SFDisplay-bold p-0 m-0">US$ {{car.detail.price.amount}}</p>
          </div>
        </div>
        <div class="divider"></div>
        <div class="p-0">
          <div class="flex items-center uppercase SFDisplay-medium pt-3 pb-1">
            <div class="p-0">
              <p class="card-details-color uppercase SFDisplay-medium p-0 m-0">ver detalles de modelo</p>
            </div>
            <div class="p-0 ml-auto">
              <i class="text-xl card-details-color ri-arrow-right-line mr-2"></i>
            </div>
          </div>
          <div class="mt-2">
            <p class="p-0 pb-2 card-advise">Imágenes meramente ilustrativas no reportando la realidad exacta, pudiendo existir variaciones en la percepción.</p>
          </div>
        </div>
      </div>
    </div>
  </NuxtLink>
</template>

<script>
  export default {
    props: ['car'],
    data () {
      return {
        img: `https://s3.sa-east-1.amazonaws.com/simplimotos-stg.com/${this.car.gallery[0].large}`,
        redirect: `/cars/${this.car.id}`
      } 
    },
    filters: {
      formatPrice: function (value) {

      }
    }
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
  .card-details-color{
    color: #c3002f;
  }
  .card-advise{
    color: #c1c1c1;
    font-size: 13px;
  }
</style>