<template>
  <div id="app">
    <AxiosComp/>
  </div>
</template>

<script>
import AxiosComp from '@/components/AxiosComp.vue';

export default {
  name: 'App',
  components: {
    AxiosComp,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>