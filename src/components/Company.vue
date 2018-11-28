<template>
  <div class="name">
    <h1 class="name">{{name}}</h1>
    <h2>{{subtitle}}</h2>
  </div>
</template>
<script>
import SpinnerButton from './spinnerbutton'
export default {
  name: 'company',
  components: { SpinnerButton },
  data(){
    return {
      name: 'flights.com',
      subtitle: 'where you can find every flight you need! and more!',
    }
  }
}
</script>
<style scoped>
.name{
  /* color: rgb(60, 85, 10); */
  font-weight: 700;
  /* background-color: rgba(196, 105, 105, 0.705); */
}
</style>

