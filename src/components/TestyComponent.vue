<template>
  <div>
    <ul>
        <li v-for='(cat, index) in cats' :key="index">{{cat.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TestyComponent',
  props: {
    cats: Array
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
