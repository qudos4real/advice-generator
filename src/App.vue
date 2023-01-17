<template>
  <!-- <router-view/> -->
  <div class="container">
    <p>Advice #{{ id }}</p>

    <p @click="log">press UP</p>
  </div>
  <!-- <p>{{ info.slip.advice }}</p> -->
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      info: {},
      id: 0,
      advice: "",
    };
  },
  methods: {
    log() {
      console.log(this);
    },
  },
  mounted() {
    console.log("Hello World");
    axios
      .get("https://api.adviceslip.com/advice")
      .then((response) => (this.info = response.data))
      .catch((error) => console.log(error));
    this.id = this.info.slip.id;
    this.advice = this.info.slip.advice;
    console.log(this.id);
    console.log(this.advice);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
