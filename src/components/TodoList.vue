<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-12">
        <ul class="list-group">
          <TodoItem
            v-for="todo in todos"
            :key="todo.id"
            :item="todo"
          />
          <TodoActions
            v-if="todos.length > 0"
          />
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import { inject } from '@vue/runtime-core';
import TodoItem from './TodoItem.vue';
import TodoActions from './TodoActions.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
    TodoActions
  },
  setup() {
    const todos = inject('todos');

    return{
      todos
    }
  }
}
</script>

<style lang="scss">
  .list-group{
    box-shadow: 0px 10px 5px $very_dark_blue;
  }
</style>