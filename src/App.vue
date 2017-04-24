<template>
  <div id="app">
    <Layout />
  </div>
</template>

<script>
import Layout from './components/Layout';

export default {
  name: 'app',
  components: {
    Layout
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
body {
  margin: 0;
}
</style>
