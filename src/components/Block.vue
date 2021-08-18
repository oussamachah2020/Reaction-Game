<template>
  <div class="block" v-if="ShowBlock" @click="stopTimer">
    click here
  </div>
</template>

<script>
export default {
  name: 'Block',
  props: ['delay'],
  data () {
    return {
      ShowBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted () {
    setTimeout(() => {
      this.ShowBlock = true
      console.log(this.delay)
      this.startTimer()
    }, this.delay)
  },

  methods: {
    startTimer () {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },

    stopTimer () {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
      console.log(this.reactionTime)
    }
  },

  updated () {
    console.log('Component Updated')
  }
}
</script>

<style scoped>
  .block {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    text-align: center;
    position: relative;
    top: 40px;
    background: rgb(17, 168, 130);
    margin:0 40px 0 40px;
    border-radius: 30px;
    padding: 5pc;
    color: #fff;
    font-weight: bold;
    letter-spacing: 3px;
  }
</style>
