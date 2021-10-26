<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me!</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  }
}
</script>

<style>
.block {
  border-radius: 35px;
  background-color: #17B978;
  color: white;
  cursor: pointer;
  font-size: 2.5rem;
  text-transform: uppercase;
  margin: 3rem auto;
  padding: 6rem 0;
  width: 500px;
  text-align: center;
}
</style>