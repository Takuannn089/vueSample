<template>
  <div>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <NewPage msg="Welcome to Your Vue.js App" msg2="HelloWorld!"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import NewPage from './components/NewPage.vue'

export default {
  name: 'App',
  components: {
    NewPage
  }
}

</script>

<!-- <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
-->
