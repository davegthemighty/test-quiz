<template>
  <div>
    <b-jumbotron >
      <template v-slot:header>Completed!</template>

      <template v-slot:lead>
        {{calculateResults()}}
      </template>

    </b-jumbotron>
  </div>
</template>

<script>

export default {
  props: {
    calculateResults: Function
  },
}

</script>
