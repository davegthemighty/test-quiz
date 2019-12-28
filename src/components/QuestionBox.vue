<template>
  <div>
    <b-jumbotron >

      <template v-slot:lead>
        {{currentQuestion.question}}
      </template>

      <hr class="my-4">

      <div>
        <b-list-group v-for="(answer, index) in answerList" v-bind:key="index">
          <b-list-group-item
              button
              v-bind:active="!currentResult.submitted && currentResult.selectedAnswer == answer"
              v-bind:variant="listItemVariant(answer)"
              @click.stop.prevent="currentResult.submitted"
              @click="currentResult.selectedAnswer = answer"
          >
              {{ answer }}
          </b-list-group-item>
        </b-list-group>
      </div>

      <div class="mt-2">
        <b-button variant="primary" v-bind:class="{ disabled: currentResult.selectedAnswer ==  '' || currentResult.submitted}" href="#" @click="submitAnswer"  class="mr-1">Submit</b-button>
        <b-button variant="secondary" v-bind:class="{ disabled: currentResult.submitted ==  false}" href="#" @click="nextQuestion">Next</b-button>
      </div>

    </b-jumbotron>
  </div>
</template>

<script>

import shuffle from 'lodash.shuffle'

export default {
  props: {
    currentQuestion: Object,
    currentResult: Object,
    nextQuestion: Function,
    submitAnswer: Function
  },
  methods: {
    listItemVariant(answer) {
        if (this.currentResult.submitted == false) {
          return ''
        }
        if (this.currentResult.selectedAnswer == answer && !this.currentResult.correct) {
          return 'danger'
        }
        if (answer == this.currentQuestion.correct_answer) {
          return 'success'
        }
        return ''
    },
  },
  computed: {
    answerList() {
      const answers = [].concat(this.currentQuestion.incorrect_answers, [this.currentQuestion.correct_answer])
      return shuffle(answers)
    },
  },
}

</script>
