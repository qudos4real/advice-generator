<template>
  <div class="container">
    <!-- <p>Advice #{{ id }}</p> -->


    <p @click="log">press UP</p>
    </div> 
    <!-- <p>{{ info.slip.advice }}</p> -->
</template>

<script>
import axios from 'axios'
export default {
name: 'MainView',
data() {
  return {
    info: {},
    id: 0,
    advice: ''
  }
},
methods: {
  log() {
    console.log(this)
  }
},
mounted() {
  console.log('Hello World')
  axios
    .get('https://api.adviceslip.com/advice')
    .then(response => (this.info = response.data))
    .catch(error => console.log(error))
  this.id = this.info.slip.id
  this.advice = this.info.slip.advice
  console.log(this.id)
  console.log(this.advice)

}
}
</script>

<style>
.container {
  margin: 50% auto;
  width: 90%;
  max-width: 400px;
  padding: 0 1rem;
  border: 1px solid blue;
}
</style>