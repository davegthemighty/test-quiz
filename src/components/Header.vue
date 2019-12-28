<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>Test Quiz</b-nav-item>
      <b-nav-item disabled>Answered {{questionIndex}} out of 10 Questions</b-nav-item>
    </b-nav>
  </div>
</template>


<script>

export default {
  props: {
    questionIndex: {
        type: Number,
        default: 0
      },
  },
}

</script>
