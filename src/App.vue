<template>
  <div
  class="position-relative"
  :style="{
    backgroundImage: 'url(' + require('@/assets/bg-desktop-dark.jpg') + ')',
    backgroundPosition: 'center',
    backgroundSize: 'cover',
    height: '300px'
  }">    
    <div class="position-absolute m-negative-t w-100">
      <div class="container">
        <div class="row">
          <div class="col-12 col-md-10 offset-md-1">
            <TodoNav
              title="T O D O"
            />
            <TodoForm />
            <TodoList />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, provide } from 'vue';
import TodoNav from './components/TodoNav.vue'
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoNav,
    TodoForm,
    TodoList
  },
  setup() {
    const todoList = ref([]);
    provide('todos', todoList);
  }
}
</script>
<style lang="scss">
  .m-negative-t{
    margin-top: 5%;
  }
</style>