<template>
  <div>
    <div>Red: {{ tallyRed }}</div>
    <div>Blue: {{ tallyBlue }}</div>
  </div>
</template>

<script>
export default {
  name: 'Tally',
  props: {
    tallyRed: Number,
    tallyBlue: Number
  }
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
