<template>
  <ul class="list-group mx-3">
    <todo-item v-for="todo in todos" :key="todo.id" :todo="todo"/>
    <todo-footer v-if="todos.length !== 0 "/>
    <todo-filter />
  </ul>
</template>

<script>
import { computed, inject, provide, ref } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFilter from './TodoFilter.vue'

export default {
  components: { TodoItem, TodoFooter, TodoFilter },
  setup(){
    const todosTodos = inject('todos')
    const filtro = ref('all')

    const todos = computed( () => {
      if (filtro.value === 'all'){
        return todosTodos.value
      }
      if (filtro.value === 'active'){
        return todosTodos.value.filter( item => item.estado === false )
      }
      if (filtro.value === 'completed') {
        return todosTodos.value.filter( item => item.estado === true )
      }
    })


    provide('filtro', filtro)

    return { todos  }
  }
}
</script>

<style>

</style>
