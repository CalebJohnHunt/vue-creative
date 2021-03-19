<template>
  <div id="app">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/create">Create</router-link> |
      <router-link to="/palette">Palette</router-link>
    </div>
    <router-view/>
    <Footer />
  </div>
</template>

<script>
import Footer from './components/Footer.vue'

export default {
  components: {
    Footer,
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  /* color: #2c3e50; */
  color: #1099b9;
}

#nav a.router-link-exact-active {
  padding: 10px;
  border-radius: 10px;
  background-color: #1099b9;
  color: white;
}

button {
  color: white;
  background-color: #1099b9;
}
</style>
