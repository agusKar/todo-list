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
            v-if="todosTodos.length > 0"
          />
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import { inject, ref, computed, provide } from 'vue';
import TodoItem from './TodoItem.vue';
import TodoActions from './TodoActions.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
    TodoActions
  },
  setup() {
    const todosTodos = inject('todos');

    const filter = ref('all');

    const todos = computed(() => {
      if(filter.value === 'all'){
        return todosTodos.value;
      }
      if(filter.value === 'active'){
        return todosTodos.value.filter(item => item.done !== true);
      }
      if(filter.value === 'completed'){
        return todosTodos.value.filter(item => item.done !== false);
      }
    });
    
    provide('filter', filter);

    return{
      todos,
      todosTodos
    }
  }
}
</script>

<style lang="scss">
  .list-group{
    border-radius: 20px!important;
    box-shadow: 0px 10px 16px 2px #0000002b;
  }
</style>