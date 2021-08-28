<template>
  <div class="pb-4">
    <div class="store-title d-flex align-items-center">
      <div class="container">
        <p class="h1 py-4 uppercase SFDisplay-black text-white store-title-p"> ¿Cuál va a ser tu próximo nissan?</p>
      </div>
    </div>
    <div class="container">
      <div>
        <p> Hola soy una p </p>
      </div>
      <div class="row container">
        <CarCard />
        <CarCard />
        <CarCard />
      </div>
      <p class="legal py-5">*Los precios expuestos en este catalogo son expresados en dólares americanos. Los mismos incluyen IVA y podrán variar en función al modelo y/o versión elegida. El precio por unidad reflejado en este catálogo refiere a la unidad de versión más económica por cada modelo. RALITOR SA se reserva el derecho de modificar y actualizar los mismos en cualquier momento. Es responsabilidad del cliente confirmar al momento de su compra, el precio final que aparece en el catálogo. No se incluyen Gastos de empadronamiento ni cualquier tipo de costo municipal, así como tampoco gastos de traslados, fletes o seguro del vehículo. No incluye costos de instalación de accesorios.</p>
    </div>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style scoped>
  .store-title{
    background-color: #ccc;
    height: 178px;
    padding: 0;
  }
  .store-title-p{
    font-size: 49px;
    font-weight: 900;
  }
  .legal{
    font-size: 14px;
    line-height: 17px;
    color: #c1c1c1;
  }
</style>