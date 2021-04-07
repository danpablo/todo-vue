<template>
  <form class="mx-3" @submit.prevent="formulario" >
    <input v-model.trim="tarea" class="form-control my-3" type="text" placeholder="Ingrese tarea">
  </form>
</template>

<script>
import { inject, ref } from '@vue/runtime-core'
export default {
  setup(){
    const todos = inject('todos')
    const tarea = ref('')
    const formulario = () => {
      if(tarea.value === ''){
        console.error('Tarea vacia')
        return
      }
      
      const todo = {
        tarea: tarea.value,
        estado: false,
        id: Date.now()
      }

      tarea.value = ''
      todos.value.push(todo)
      
    }

    return { formulario, tarea }
  }
}
</script>

<style>

</style>
