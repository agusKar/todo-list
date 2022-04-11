<template>
  <li class="list-group-item list-item-dark py-3 d-flex align-items-center justify-content-between">
    <div>
      <span>5 items left</span>
    </div>
    <div class="list-actions">
      <a href="">All</a> 
      <a href="">Active</a> 
      <a href="" class="active">Completed</a>
    </div>
    <div>
      <a href="">Clear completed</a>
    </div>
  </li>
</template>
<script>
import { inject } from 'vue'
export default {
  setup() {
    const todos = inject('todos');

    return{
      todos
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
    a{
      text-decoration: none;
      color: $dark_grayish_blue;
      &:hover{
        color: $light_grayish_blue;
      }
    }
    .list-actions a{
      margin-right: 0.6rem;
      &.active{
        color: $light_grayish_blue;
      }
    }
  }
</style>