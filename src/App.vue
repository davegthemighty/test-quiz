<template>
  <div id="app">
    <Header/>
    <QuestionPanel
        :v-if="questions.length"
        :question="questions[questionIndex]"
        :next="next"
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
    }
  },
  methods: {
    next() {
      this.questionIndex++
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
