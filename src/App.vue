<template>
  <h1 class="title">Reaction Timer</h1>
  <p class="instructions">This is simple test to measure your reaction time. To start, click on the Play! button below. After some time a big block will appear. Click on it as fast as possible to measure how quickly your brain processes visual information!</p>
  <button class="play-btn" @click="start" :disabled="isPlaying">Play!</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #626079;
  margin: 3.5rem 2rem;
}

.title {
  font-size: 3.3rem;
  letter-spacing: 1px;
  margin-bottom: 1.5rem;
}

.instructions {
  letter-spacing: 1px;
  line-height: 1.7;
  margin: 0 auto;
  max-width: 35rem;
}

.play-btn {
  background: #F6F6F6;
  border: 3px solid #8785A2;
  border-radius: 15px;
  color: #8785A2;
  cursor: pointer;
  font-size: 2rem;
  margin-top: 2rem;
  padding: .5rem 1.5rem;
  font-family: 'Poppins', sans-serif;
  text-transform: uppercase;
  transition: all .2s ease-out;
}

.play-btn:hover {
  background: #8785A2;
  color: #F6F6F6;
}

button[disabled] {
  opacity: .2;
  cursor: not-allowed;
}
</style>
