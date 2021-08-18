<template>
  <div>
    <p>{{rank}}</p>
  </div>
</template>

<script>
export default {
  name: 'Rank',
  props: ['score'],
  data () {
    return {
      rank: null
    }
  },

  mounted () {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers'
    } else if (this.score < 400) {
      this.rank = 'Rapid flexes'
    } else {
      this.rank = 'Snail Pace...'
    }
  }
}
</script>

<style scoped>
p {
  color: rgb(21, 233, 21);
  font-size: 25px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  text-align: center;
  font-weight: bold;
}
</style>
