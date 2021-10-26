<template>
  <div class="results">
    <p>Reaction time: <span class="score">{{ score }}</span> ms</p>
    <p class="rank"> {{ rank }} </p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 240) {
      this.rank = 'Flash would be proud!'
    } else if (this.score < 300) {
      this.rank = 'Lightspeed!'
    } else if (this.score < 400){
      this.rank = 'You may want to practice this a bit?'
    } else {
      this.rank = 'Not bad... for a snail.'
    }
  }
}
</script>

<style>

.results {
  margin-top: 1.5rem;
  font-size: 2rem;
}

.score {
  font-weight: 600;
}

.rank {
  font-style: italic;
}
</style>