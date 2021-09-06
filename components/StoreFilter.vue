<template>
  <div class="mt-4 md:mr-4">
    <button :id="filter.name" class="text-black SFDisplay-medium flex flex-row items-center
      font-medium py-3 px-5 border border-gray-200 rounded-lg uppercase text-sm" :disabled="filterPicked" @click="abrirDialog()">
      {{filter.name}}
      <i class="ri-arrow-down-s-line text-xl" v-if="!filterSelect"></i>
      <i class="ri-arrow-up-s-line text-xl" v-else></i> 
    </button>
    <div v-if="filterSelect" class="text-black flex flex-col absolute z-10 w-56 p-5
      border border-gray-200 rounded-lg uppercase text-sm bg-white">
      <p>{{filter.name_dialog}}</p>
      <form class="mt-3">
        <div v-for="(select, index) in filter.select" :key="select">
          <label>
            <input v-model="filterSelected" :value="filter.values[index]" type="radio">
              {{select}}
          </label>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['filter', 'referencia'],
    data() {
      return {
        filterSelect: false,
        filterPicked: false,
        filterSelected: ""
      }
    },
    methods: {
      abrirDialog(){
        this.filterSelect = this.filterSelect ? false : true
      }
    },
    watch: {
      filterSelected: function(val){
        if(!val) return false

        const { name } = this.filter
        this.filterSelect = false
        this.filterPicked = true
        const data = {
          name,
          value: val,
          ref: this.referencia
        }
        this.$emit('filtroStore', data)
      },
      filterPicked: function(val) {
        const { name } = this.filter
        const element = document.getElementById(name)
        if(val == true){
          element.classList.add("disabled")
        }else{
          element.classList.remove("disabled")
        }
      }
    }
  }
</script>

<style scoped>
  .disabled{
    background-color: #ccc;
    color: black;
  }
</style>