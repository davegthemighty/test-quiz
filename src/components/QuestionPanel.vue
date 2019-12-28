<template>
  <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
              v-if="question"
              :currentQuestion="question"
              :currentResult="result"
              :nextQuestion="next"
              :submitAnswer="submitAnswer"
          />
          <ResultsBox
              v-if="questionIndex == 10"
              :calculateResults="calculateResults"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

import QuestionBox from './QuestionBox.vue'
import ResultsBox from './ResultsBox.vue'
export default {
  name: 'QuestionPanel',
  components: {
    QuestionBox,
    ResultsBox
  },
  props: {
    question: Object,
    result: Object,
    next: Function,
    submitAnswer: Function,
    calculateResults: Function,
    questionIndex: {
        type: Number,
        default: 0
      },
  },
}

</script>
