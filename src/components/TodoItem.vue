<template>
  <li class="list-group-item list-item-dark py-3 d-flex align-items-center justify-content-between">
    <!-- text and image of the item -->
    <div
      role="button"
      class="img_check"
      :class="{'itemDone': item.done}"
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
    >
      <img
        src="@/assets/icon-cross.svg"
        alt="icon delete">
    </div>
  </li>
</template>
<script>
export default {
  props: {
    item: {
      type: Object,
      require: true
    }
  }
}
</script>

<style scoped lang="scss">
  .list-item-dark{
    background-color: $very_dark_desaturated_blue!important;
    color: $light_grayish_blue;
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
      border: 2px solid $very_dark_grayish_blue;
      flex: none;
      &:hover{        
        background: linear-gradient($very_dark_desaturated_blue, $very_dark_desaturated_blue) padding-box, linear-gradient(to right, hsl(192, 100%, 67%), hsl(280, 87%, 65%)) border-box;
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
      color: $dark_grayish_blue;
    }
  }
  .img_cross{
    opacity: 0.6;
    &:hover{
      opacity: 1;
    }
  }
</style>