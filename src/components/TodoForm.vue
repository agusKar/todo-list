<template>
  <div class="container">
    <form
      @submit.prevent="onSubmit"
      class="text-center"
    >
      <input
        class="form-control form-control-lg border-0 text-white mt-3"
        type="text"
        v-model.trim="newItem"
        placeholder="Add new item"
        name="newItem"
        id="newItem"
      >
      <label class="form-check-label text-secondary mt-1" for="newItem">(Press <i>enter</i> to <b>Save</b>)</label>
    </form>
  </div>
</template>
<script>
import { inject, ref } from 'vue';
export default {
  setup() {
    // Data
    const newItem = ref('');
    const todos = inject('todos');

    // Methods
    const onSubmit = () => {
      if(newItem.value !== ''){
        const todo = {
            id: Date.now(),
          name: newItem.value,
          done: false
        };
        todos.value.push(todo);
        newItem.value = '';
      }
    };

    return{
      onSubmit,
      newItem
    }
  },
}
</script>
<style lang="scss">
  input{
    background-color: $very_dark_desaturated_blue!important;
    box-shadow: 0px 0px 6px 0px hsl(235deg 21% 11%);
  }
</style>