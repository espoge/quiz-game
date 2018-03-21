<template>
  <div id="app">
    <intro v-show="showTop" v-on:startQuiz="startQuiz"/>
      <question :questionList='questionList'v-show="showQuestion" />
  </div>
</template>

<script>

import Question from './components/Question'
import Intro from './components/Intro'
export default {
  name: 'App',
  data:function () {
    return {
      showTop: true,
      showQuestion: false,
        questionList: [
        {
          title: 'What is the colour of unoxidized blood?',
          answers: [
              {answer: 'Blue'},
              {answer: 'Red'},
              {answer: 'Purple'},
              {answer: 'Green'},
          ],
          correct: 1
        },
        {
          title: 'Which of the following passenger jets is the longest?',
          answers: [
              {answer: 'Airbus A350-1000'},
              {answer: 'Boeing 787-10'},
              {answer: 'Boeing 747-8'},
              {answer: 'Airbus A350-1000'}
          ],
          correct: 2
        },
        {title: 'Which of these bands is the oldest?',
        answers: [
            {answer: 'AC/DC'},
            {answer: 'Metallica'},
            {answer: 'Red Hot Chili Peppers'},
            {answer: 'Pink Floyd'}
        ],
        correct: 3
      },
      {title: 'What year was the United States Declaration of Independence signed?',
      answers: [
          {answer: '1775'},
          {answer: '1776'},
          {answer: '1777'},
          {answer: '1774'}
      ],
      correct: 1
    },
    {title: 'Velma Kelly and Roxie Hart are the protagonists of which Oscar winning movie?',
    answers: [
        {answer: 'Chicago'},
        {answer: 'Cabaret'},
        {answer: 'Dreamgirls'},
        {answer: 'All That Jazz'}
    ],
    correct: 0
  },
    ],

    };
  },
  methods:{
    startQuiz(){
      this.showTop=false,
      this.showQuestion=true
    },

  },
  components: {
    'question': Question,
    'intro' : Intro
  }
}
</script>
<style media="screen">
  @import '/assets/vue2-animate.min.css';

  html {
      background-color: #4481eb;
        background-image: linear-gradient(0deg,#5AD6FE 0,#00B2FE);
        background-repeat: no-repeat;
        font-family: 'Roboto', sans-serif;
  }
  #app {
  width: 500px;
  height: 580px;
  display: block;
  margin: 0 auto;
  background-color: #0093C6;
  border-radius: 20px;
  padding: 20px;
  text-align: center;
  color: #fff;

  }
</style>
