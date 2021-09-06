<template>
  <div class="grid grid-cols-1">
      <nav class="flex flex-row items-center">
        <NuxtLink to="/"><img src="~/assets/img/brand.svg" /></NuxtLink>
        <div class="desktop hidden md:flex flex-row ">
          <ul class="list-none mb-0 flex flex-row items-center ml-8 gap-x-6">
            <NavLink v-for="link in links" :key="link.name" :link="link" />
          </ul>
          <div class="search-bar">
            <form>
              <input id="search" class="form-control SFDisplay uppercase" placeholder="buscar por modelo o vehiculo" type="text">
            </form>
          </div>
        </div>
        <div class="block md:hidden absolute right-5" @click="OpenCloseMenu()">
          <i v-if="!openMenu" class="ri-menu-line text-4xl p-0"></i> 
        </div>
      </nav>
      <div v-if="openMenu" class="flex flex-col md:hidden w-full h-auto fixed bg-white z-50">
        <div class="flex flex-row items-center">
          <NuxtLink to="/"><img src="~/assets/img/brand.svg" /></NuxtLink>
          <div class="block md:hidden absolute right-5" @click="OpenCloseMenu()">
            <i class="ri-close-line text-4xl p-0"></i> 
          </div>
        </div>
        <div class="container flex flex-col uppercase justify-start text-left pt-5">
          <p class="pb-4 SFDisplay-heavy text-gray-600">¿Cuál va a ser tu próximo Nissan?</p>
          <NuxtLink class="pb-4 SFDisplay-light text-black" to="/store">Vehículos</NuxtLink>
          <NuxtLink class="pb-4 SFDisplay-light text-black" to="/">Descrubrí Nissan</NuxtLink>
          <div class="divider"></div>
          <form class="my-4">
            <input id="search" class="form-control SFDisplay uppercase" placeholder="buscar por modelo o vehiculo" type="text">
          </form>
        </div>
      </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        links : [
          {
            "name" : "vehículos",
            "src" : "/store"
          },
          {
            "name" : "descubrí  nissan",
            "src" : "/"
          }
        ],
        openMenu: false
      }
    },
    methods : {
      OpenCloseMenu(){
        this.openMenu = this.openMenu ? false : true
      },
    }
  }
</script>

<style scoped>
.divider{
  border-top: 1px solid #e3e2e2;
}
.search-bar{
  position: absolute;
  right: 15px;
  top: 20px;
}
#search {
  background-image: url(~/assets/img/search.svg);
  background-repeat: no-repeat;
  background-position: 15px;
  border: none;
  border-radius: 10px;
  background-color: hsla(0,0%,100%,.8);
  width: 323px;
  height: 60px;
  float: right;
  padding-left: 50px;
  font-size: 13px;
}
.form-control{
  display: block;
  width: 100%;
  height: calc(1.5em + .75rem + 2px);
  padding: .375rem .75rem;
  padding-left: 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: .25rem;
  transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
.form-control:focus {
  color: #495057;
  background-color: #fff;
  border-color: #80bdff;
  outline: 0;
  box-shadow: 0 0 0 .2rem rgba(0,123,255,.25);
  outline: 0 !important;
  box-shadow: none !important;
}
</style>