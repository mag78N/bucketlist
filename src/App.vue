<template>
  <div id="app">
    <img class="logo" alt="Maphacking logo" src="./assets/maphacking-logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <List></List>
  </div>
</template>

<script>
import List from './components/List.vue';

export default {
  name: 'App',
  components: {
    List,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #032e3e;
  padding: 25px 0;
}
.logo {
  max-height: 60px;
}
</style>
