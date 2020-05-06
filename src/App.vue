<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Portfolio msg="An amazing Vue project"/>
    <p>Consultando... {{ url }}</p>
    <p>Info recibida <span>&#128071;</span></p>
    <pre id="api-info">{{ info }}</pre>
  </div>
</template>

<script>
import Portfolio from './components/Portfolio.vue'
import axios from "axios";

export default {
  name: 'App',
  components: {
    Portfolio
  },
  data () {
    return {
      url: null,
      info: null
    }
  },
  mounted () {
    this.url = 'http://localhost:8081/saludo';
    axios
      .get(this.url)
      .then(response => (this.info = response))
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

#api-info {
  text-align: left;
}  
</style>
