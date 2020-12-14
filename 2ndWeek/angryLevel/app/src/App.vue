<template>
  <div id="app">
    <Title msg="怒らせろ！"/>

    <div v-if="counter > 5 && counter <= 30">
        <img src="./assets/angry2.png" alt="">
      </div>
      <div v-else-if="counter >= 30 && counter <= 60">
        <img src="./assets/angry3.png" alt="">
      </div>
      <div v-else-if="counter >= 60 && counter <= 99">
        <img src="./assets/angry4.png" alt="">
      </div>
      <div v-else-if="counter >= 99">
        <img src="./assets/angry5.png" alt="">
      </div>
      <div v-else>
        <img src="./assets/angry1.png" alt="">
      </div>
      
      <div class="status">
        <button class="btn btn-danger" v-on:click="counter+=5">押せ！</button>
        怒り指数 {{ counter }}
      </div>
  </div>
</template>

<script>
import Title from './components/Title.vue'

export default {
  name: 'App',
  components: {
    Title
  },
  data() {
    return {
      counter: 0
    }
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

.status {
  font-size: 3rem;
}
</style>
