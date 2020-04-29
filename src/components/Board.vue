<template>
  <div>
    <div>Board id: {{ bid }}, isSpyMaster: {{ isSpyMaster }}, spyMasterCode: {{ code }}</div>
    <ul>
      <li v-for="(w, i) in words" :key="i">
        <div @click="cardClick(w)">{{ w }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Board',
  props: {
    boardId: String,
    width: Number,
    isSpyMaster: Boolean,
    spyMasterCode: String
  },
  data: function() {return{
    words: [],
    bid: this.$props.boardId,
    code: this.$props.spyMasterCode
  }},
  mounted: function() {
    this.words = this.randomWords(5)
  },
  watch: {
    boardId: function(value, old) {
      this.bid = value
      this.words = this.randomWords(5)
    },
    spyMasterCode: function(value, old) {
      this.code = value
    }
  },
  methods: {
    randomWords: function(amount = 1) {
      // seed = boardId
      return [1,2,3,4,this.bid]
    },
    matrix: function(elements) {
      // this.width
      return [[1,2],[3,4]]
    },
    cardClick: function(value) {
      console.log(value)
    }
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
