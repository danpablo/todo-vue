<template>
  <li class="list-group-item d-flex justify-content-between align-items-center"> 
    <span role="button" @click="completar(todo.id)" 
          :class="{ 'tachado': todo.estado }">
      {{ todo.tarea }}
    </span>  
    <span role="button" @click="eliminar(todo.id)">
      <i class="fas fa-trash"></i>
    </span>  
  </li>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  setup(){
    const todos = inject('todos')
    
    const eliminar = (id) => {
      todos.value = todos.value.filter( (item) => item.id !== id )
    }

    const completar = (id) => {
      todos.value = todos.value.map( item => {
        if(item.id === id){
          item.estado = !item.estado
        }

        return item

      })
    }

    return { eliminar, completar }

  }

}
</script>

<style>
.tachado {
    text-decoration: line-through;
}

</style>
