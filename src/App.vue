<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <poker-game></poker-game>
</template>

<script>
import PokerGame from './components/PokerGame.vue'
export default {
  name: 'App',
  components: {
    PokerGame
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
</style>
