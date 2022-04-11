<template>
  <div class="container">
    <div class="row align-items-center justify-content-between">
      <div class="col-6">
        <h1>{{ title }}</h1>
      </div>
      <div class="col-6 text-end">
        <img
          role="button"
          src="@/assets/icon-sun.svg" 
          alt="icon-sun"
          @click="changeTheme"
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      require: true
    },
  },
  setup(){
    // Methods
    const changeTheme = () =>{
      console.log("change theme")
    }
    return {
      changeTheme
    }
  }
}
</script>
<style lang="scss">
  h1{
    font-weight: bold;
    margin: 0;
  }
</style>
