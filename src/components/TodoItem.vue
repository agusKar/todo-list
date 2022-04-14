<template>
  <li class="list-group-item list-item-dark py-3 d-flex align-items-center justify-content-between">
    <!-- text and image of the item -->
    <div
      role="button"
      class="img_check"
      :class="{'itemDone': item.done}"
      @click="changeStatus(item.id)"
      >
      <div>
        <img
          v-if="item.done"
          src="@/assets/icon-check.svg"
          alt="icon check">
      </div>
      <span>{{ item.name }}</span>
    </div>
    <!-- Img to delete item -->
    <div 
      class="img_cross float-right"
      role="button"
      @click="deleteItem(item.id)"
    >
      <img
        src="@/assets/icon-cross.svg"
        alt="icon delete">
    </div>
  </li>
</template>
<script>
import { inject } from 'vue';
export default {
  props: {
    item: {
      type: Object,
      require: true
    }
  },
  setup() {
    const todos = inject('todos');

    const changeStatus = id => {
      todos.value.map(item => {
        if(item.id === id){
          item.done = !item.done;
        }
      })
    };

    const deleteItem = id => {
      todos.value = todos.value.filter(item => item.id != id);
    };

    return {
      changeStatus,
      deleteItem
    }
  }
}
</script>

<style scoped lang="scss">
  .list-item-dark{
    background-color: var(--bg-primary)!important;
    color: var(--text-primary);
  }
  .img_check{
    display: flex;
    align-items: center;
    justify-content: space-around;
    span{
      text-transform: capitalize;
    }
    div{
      margin-right: 1rem;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      border: 2px solid var(--bg-secondary);
      flex: none;
      &:hover{        
        background: linear-gradient(var(--bg-primary), var(--bg-primary)) padding-box, linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%)) border-box;
        border: 2px solid transparent;
      }
      img{
        width: 15px;
      }
    }
  }
  .itemDone{
    div{
      background: $gradient;
    }
    span{
      text-decoration: line-through;
      color: var(--text-gray);
    }
  }
  .img_cross{
    opacity: 0.6;
    &:hover{
      opacity: 1;
    }
  }
</style>