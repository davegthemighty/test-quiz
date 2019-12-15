<template>
  <div>
    <b-jumbotron >

      <template v-slot:lead>
        {{question}}
      </template>

      <hr class="my-4">

      <p>
        The Answers
      </p>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="secondary" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>


<script>

export default {
  name: 'QuestionBox',
  props: [
    'question'
  ],
}

</script>
