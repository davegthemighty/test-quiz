<template>
  <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>


<script>
import QuestionBox from './QuestionBox.vue'

export default {
  name: 'QuestionPanel',
  components: {
    QuestionBox
  },
}

</script>
