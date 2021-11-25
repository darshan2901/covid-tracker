<template>
  <div class="container">
    <the-header></the-header>
    <router-view/>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';

export default{
  components: { TheHeader },
}
</script>

<style scoped>
.container{
  text-align: center;
  padding: 40px;
}
</style>
