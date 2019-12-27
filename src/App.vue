<template>
  <div id="app">
    <Header/>
    <QuestionPanel
        :v-if="questions.length"
        :question="questions[questionIndex]"
        :result="results[questionIndex]"
        :next="next"
        :submitAnswer="submitAnswer"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionPanel from './components/QuestionPanel.vue'

export default {
  name: 'app',
  components: {
    Header,
    QuestionPanel
  },
  data() {
    return {
      questions: [],
      questionIndex: 0,
      results: Array(10).fill(null).map(() => (
      {
        selectedAnswer: "",
        submitted: false,
        correct: false,
      })),
    }
  },
  methods: {
    next() {
      this.questionIndex++
    },
    submitAnswer() {
        const result = this.results[this.questionIndex]
        result.submitted = true
        result.correct = result.selectedAnswer == this.questions[this.questionIndex].correct_answer
    }
  },
  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10&category=27&type=multiple', {
      method: 'get',
    }).then((response) => {
      return response.json()
    }).then((jsonData) => {
      this.questions = jsonData.results
    })
  },
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
