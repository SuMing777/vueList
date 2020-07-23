<template>
  <div id="app">
    <parent/>
  </div>
</template>

<script>
import parent from './component/parent.vue';
export default {
  name: 'App',
  components: {
    parent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
