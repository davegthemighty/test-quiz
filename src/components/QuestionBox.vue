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
              v-bind:class="{ active: selectedAnswer ==  answer}"
              @click="selectedAnswer = answer"
          >
              {{ answer }}
          </b-list-group-item>
        </b-list-group>
      </div>

      <div class="mt-2">
        <b-button variant="primary" v-bind:class="{ disabled: selectedAnswer ==  ''}" href="#" class="mr-1">Submit</b-button>
        <b-button variant="secondary" v-bind:class="{ disabled: selectedAnswer ==  ''}" href="#" @click="nextQuestion">Next</b-button>
      </div>

    </b-jumbotron>
  </div>
</template>

<script>

import shuffle from 'lodash.shuffle'

export default {
  data() {
    return {
      selectedAnswer: "",
    }
  },
  props: {
    currentQuestion: Object,
    nextQuestion: Function
  },
  computed: {
    answerList() {
      const answers = [].concat(this.currentQuestion.incorrect_answers, [this.currentQuestion.correct_answer])
      return shuffle(answers)
    },
    isCorrect() {
      return this.currentQuestion.correct_answer === this.selectedAnswer
    },
  },
}

</script>
