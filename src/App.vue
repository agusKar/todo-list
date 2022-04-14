<template>
  <div
  class="position-relative"
  :style="{
    backgroundImage: 'url(' + require(`@/assets/${imgBgName}`) + ')',
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
            <div class="wrapper"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, provide, onBeforeMount, watchEffect } from 'vue';
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
    const imgBgName = ref('bg-desktop-light.jpg');
    const defaultTheme = ref('theme-light');
    provide('todos', todoList);
    provide('theme', defaultTheme);
    provide('imgBgName', imgBgName);

    onBeforeMount(() => {
      document.body.classList.add('theme', defaultTheme.value);
    });

    watchEffect(() => {
      document.body.classList.remove('theme-dark', 'theme-light');
      document.body.classList.add(defaultTheme.value);
    })

    return{
      imgBgName
    }
  }
}
</script>
<style lang="scss">
  .m-negative-t{
    margin-top: 5%;
  }
</style>