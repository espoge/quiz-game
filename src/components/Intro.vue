<template lang="html">
    <div class="">
      <h1>Quiz game</h1>
      <p>This is a quiz application built using VueJS. </p>
      <p>view code on <a href="https://github.com/espoge/quiz-game">github</a></p>
      <button type="button" name="button" @click="startQuiz">Start Quiz</button>
    </div>
</template>

<script>
export default {
  methods:{
    startQuiz(){
      this.$emit('startQuiz')
    }
  }
}
</script>

<style lang="css">
</style>
