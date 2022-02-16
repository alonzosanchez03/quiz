<template>
<div class="ctr">
  <Questions :questions="questions" v-if="questionsAnswered < questions.length" :questionsAnswered="questionsAnswered" :updateQA="updateQA"></Questions>
  <Result v-else :correctAnswers="correctAnswers"></Result>
    
    <button type="button" class="reset-btn" @click.prevent="resetQA">Reset</button>
</div>
</template>

<script>
import Questions from "./components/Questions.vue"
import Result from "./components/Result.vue"

export default {
  name: 'App',
  data () {
    return {
      questionsAnswered: 0,
      correctAnswers: 0,
      questions: [
        {
            q: 'What is 2 + 6?', 
            answers: [
                {
                    text: '4',
                    is_correct: false
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true
                },
                {
                    text: '5',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'How many letters are in the word "Banana"?', 
            answers: [
                {
                    text: '5',
                    is_correct: false
                },
                {
                    text: '7',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true 
                },
                {
                    text: '12',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: C_ke', 
            answers: [
                {
                    text: 'e',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: true 
                },
                {
                    text: 'i',
                    is_correct: false 
                }
            ] 
        },
      ],
      results: [
        {
            min: 0,
            max: 2,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!"
        },
        {
            min: 3,
            max: 3,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!"
        }
      ]
    }
  },
  components: {
    Questions,
    Result
  },
  methods: {
    updateQA (isCorrect) {
      if (isCorrect) {
        this.correctAnswers++
      }
      this.questionsAnswered++
    },
    resetQA () {
      this.questionsAnswered = 0
      this.correctAnswers = 0
    }
  }
}
</script>

