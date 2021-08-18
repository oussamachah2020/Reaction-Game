<template>
  <div>
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Start</button>
    <p v-if="Result">Your reaction time is {{ score }} ms</p>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Rank :score="score" v-if="Result"/>
  </div>
</template>

<script>
import Block from './components/Block'
import Rank from './components/Rank'
export default {
  name: 'App',
  components: { Block, Rank },
  data () {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      Result: false
    }
  },

  methods: {
    start () {
      this.isPlaying = true
      this.delay = Math.random() * 3000
      this.Result = false
      // console.log(this.delay)
    },
    endGame (react) {
      this.score = react
      this.isPlaying = false
      this.Result = true
    }
  }
}
</script>

<style scoped>
  h1 {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    text-align: center;
  }
  button {
    margin-left: 11pc;
    border: none;
    outline: none;
    border-radius: 8px;
    background: rgb(22, 229, 22);
    color: white;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    padding: 10px 2pc 10px 2pc;
    cursor: pointer;
    font-weight: bold;
  }
  button[disabled] {
    cursor: not-allowed;
    opacity: .4;
  }
  p {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    text-align: center;
    color: rgb(103, 101, 101);
  }
</style>
