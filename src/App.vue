<template>
  <div id="app">
   <main-page></main-page>
  </div>
</template>

<script>
import MainPage from './components/main-page.vue'

export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style>

*, ::before, ::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Avenir, Arial, Helvetica, sans-serif;
}

body {
  height:100vh;
  background: linear-gradient(to top, #a18cd1 0%, #fbc2eb 100%);
}

</style>
