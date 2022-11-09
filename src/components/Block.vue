<template>
  <div class="block" 
  :style="{ 
    width: `${this.size}px`, 
    height: `${this.size}px`,
    position: 'absolute',
    left: `${this.posX}px`,
    top: `${this.posY}px`,
    background: `rgb(${this.r}, ${this.g}, ${this.b})`
  }"
  v-if="showBlock" @click="stopTimer">
    Click Me!
  </div>
</template>

<script>
export default {
  name: 'Block',
  data() {
    return {
      color: 'blue',
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  props: ['delay', 'size', 'posX', 'posY', 'r', 'g', 'b'],
  mounted() {
    setTimeout(() => {
      this.startTimer()
      this.showBlock = true
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
      this.$emit('endGame', this.reactionTime)
    }
  }
}
</script>

<style scoped>
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  background: red;
  border-radius: 50%;
  text-align: center;
  font-size: 70%;
}
</style>