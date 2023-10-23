<template>
  <div class="container">
    <NavComp />
    <router-view></router-view>
  </div>
</template>

<script>
import NavComp from './components/NavPage.vue'
export default {
  name: 'App',
  components: {
    NavComp
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
}

.container {
  background: linear-gradient(45deg, #3a3a3a 10%, transparent 11%, transparent 89%, #3a3a3a 90%), linear-gradient(135deg, #3a3a3a 10%, transparent 11%, transparent 89%, #3a3a3a 90%), radial-gradient(circle, transparent 25%, #323232 26%), linear-gradient(45deg, transparent 46%, #3a3a3a 47%, #3a3a3a 52%, transparent 53%), linear-gradient(135deg, transparent 46%, #3a3a3a 47%, #3a3a3a 52%, transparent 53%);
  background-size: 3em 3em;
  background-color: #323232;
  opacity: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;

}
</style>
