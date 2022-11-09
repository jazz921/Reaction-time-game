<template>
  <div>
    <h1>
      The Reaction time is: {{ score }} ms
    </h1>
  </div>
</template>

<script>
  export default {
    name: 'Result',
    props: {
      score: Number,
    }
  }
</script>

<style scoped>

</style>