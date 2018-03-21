<template lang="html">
<div class="">
<div v-for="(question, index) in questionList">

<div v-if="index===questionIndex">
    <h2>{{question.title}}</h2>
    <p v-show="countQuestion != 0" id="cq">Question: {{countQuestion}} / {{questionList.length}}</p>
      <button v-for="(qst,i) in question.answers" @click="check(question.correct, i)" :class="[question.correct === i ? {'correct':correct} : {'incorrect':incorrect}, {'btnrsp': btnActive}] " :disabled="btnQuestion">{{qst.answer}}</button>

  </div>
  </div>
  <p id="score">Your score: {{total}}</p>
<transition name="fadeDown">
    <button type="button" name="button" v-show="sb" @click="nextQuestion">Next Question</button>
</transition>
  <button type="button" name="button" v-show="countQuestion === 0" @click="restart">Restart</button>

  </div>
</template>

<script>
export default {
  props:['questionList'],
  data:function () {
    return{
      risposta:'',
      correct: false,
      incorrect: false,
      questionIndex: 0,
      countScore:0,
      countQuestion: this.questionList.length,
     totalResponse: Array(0),
      ind:0,
      sb: false,
      btnQuestion:false,
      btnActive:true
    }
  },
  methods: {
    check(a, i){
    this.correct=true,
    this.incorrect=true,
    a === i ? this.totalResponse.splice(this.ind, 1, true) :  this.totalResponse.splice(this.ind, 1, false)
    this.ind++,
    this.sb=true,
    this.btnQuestion=true,
    this.btnActive=false

  },
    nextQuestion(){
      this.questionIndex++,
      this.correct=false,
      this.incorrect=false
      this.sb=false,
      this.countQuestion--,
      this.btnQuestion=false,
      this.btnActive=true
    },
    restart(){
    this.questionIndex=0,
    this.totalResponse= Array(0)
    this.countQuestion= this.questionList.length
    }

  },
  computed: {
  total(){
    var countScore = 0;
    this.totalResponse.forEach(v => v ? countScore++ : v);
      return countScore;
    }
  }
}
</script>

<style lang="css">
h2 {min-height: 60px}
p {color: #96D6F7}
button {
  display: block;
  margin: 20px auto;
  background-color: #f4f4f4;
  padding: 20px;
  border: none;
  cursor: pointer;
  width: 300px;
  border-radius: 20px;
  font-size: 16px;
  color: #292C44;
}
.btnrsp {
  -webkit-transition: all .5s; /* Safari */
    transition: all .5s;
}
.btnrsp:hover {
  transform:translateY(-4px);
  background-color: #E0E0E0;
}
.correct {
  background-color: #5cdb80;
}
.incorrect {
  background-color: #ff5593;
}
.correct, .incorrect {
  color: #fff;
}
#cq {font-size: 20px}
#score {color: #171AAC; font-size: 22px}
</style>
