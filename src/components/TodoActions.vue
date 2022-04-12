<template>
  <li class="list-group-item list-item-dark py-3 d-block d-md-flex align-items-center justify-content-between">
    <div>
      <span>{{ itemsLeft }} items left</span>
    </div>
    <div class="list-actions my-2 my-md-0">
      <span 
        role="button"
        :class="{'active': filter === 'all'}"
        @click="filterItem('all')">All</span> 
      <span 
        role="button"
        :class="{'active': filter === 'active'}"
        @click="filterItem('active')">Active</span> 
      <span 
        role="button"
        :class="{'active': filter === 'completed'}"
        @click="filterItem('completed')">Completed</span>
    </div>
    <div>
      <span
        role="button"
        @click="clearCompleted">Clear completed</span>
    </div>
  </li>
</template>
<script>
import { computed, inject } from 'vue'
export default {
  setup() {
    const todos = inject('todos');
    const filter = inject('filter');

    const itemsLeft = computed(() => {
      return todos.value.filter(item => item.done === false).length;
    })

    const clearCompleted = () => {
      todos.value = todos.value.filter(item => item.done !== true);
    };

    const filterItem = filterValue => {
      filter.value = filterValue;
    };

    return{
      todos,
      itemsLeft,
      clearCompleted,
      filterItem,
      filter
    }
  },
}
</script>

<style scoped lang="scss">
  .list-item-dark{
    background-color: $very_dark_desaturated_blue!important;
    color: $light_grayish_blue;
    font-size: 0.9rem;
    color: $dark_grayish_blue;

    span{
      margin-right: 0.6rem;
      text-decoration: none;
      color: $dark_grayish_blue;

      &[role="button"]:hover{
        color: $light_grayish_blue;
      }
      &.active{
        font-weight: bold;
        background: $gradient;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
  }
</style>