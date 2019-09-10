<template>
  <div id="app">
    <!-- router eklemek için -->
    <!-- <router-link to="/">Home</router-link> -->

    <!-- router view'ini görmek için -->
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "app"
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1,
h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}
</style>
