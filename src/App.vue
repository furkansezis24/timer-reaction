<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <BlockBir v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsBir v-if="showResultsBir" :score="score" />
</template>

<script>

import BlockBir from './components/BlockBir'
import ResultsBir from './components/ResultsBir'
export default {
  name: 'App',
  components: { BlockBir, ResultsBir },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResultsBir: false
    }
  },
  methods: {
    start() {
      
      this.delay = 1500 + Math.random() * 4500
      this.isPlaying = true
      this.showResultsBir = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResultsBir = true
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
    color: #444;
    margin-top: 60px;
  }
  button {
    background: #0faf80;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>