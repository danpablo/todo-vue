<template>
  <div class="card mt-3">
    <div class="card-body d-flex justify-content-between align-items-center">
      <span role="button" @click="filtrar('active')"> Activos </span>
      <span role="button" @click="filtrar('all')"> All </span>
      <span role="button" @click="filtrar('completed')"> Completados </span>
    </div>
  </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
  setup(){
    const filtro = inject('filtro')

    const filtrar = (estado) =>{
      filtro.value = estado
    } 
    return { filtrar }
  }



}
</script>

<style>

</style>
