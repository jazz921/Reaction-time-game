<template>
  <h1>Reaction Timer</h1>
  <p>Click the play button and a circle will appear on the screen randomly</p>
  <button class="btn" @click="play" :disabled="isPlaying">Play!</button>
  <Block v-if="isPlaying" :r="r" :g="g" :b="b" :size="size" :posX="posX" :posY="posY" :delay="delay" @endGame="endGame" />
  <Result v-if="showResults" :score="score" />
</template>

<script>
import { Block, Result } from './components'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      size: null,
      posX: null,
      posY: null,
      r: null,
      g: null,
      b: null
    }
  },
  components: {
    Block,
    Result
  },
  methods: {
    play() {
      this.delay = 1000 + Math.floor(Math.random() * 4000)
      this.size = 50 + Math.floor(Math.random() * 50)
      this.posX = Math.floor(Math.random() * 1000)
      this.posY = Math.floor(Math.random() * 500)
      this.r = Math.floor(Math.random() * 254)
      this.g = Math.floor(Math.random() * 254)
      this.b = Math.floor(Math.random() * 254)
      this.isPlaying = true
      this.score = null
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
  }
}

</script>

<style scoped>
.btn {
  margin-top: 5px;
  font-size: 18px;
  padding: 5px 10px;
}

</style>
