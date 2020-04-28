<template>
  <div id="app">
    <h1>Codewrods</h1>

    <div>
      <p>Board ID: <input v-model="boardId"></p>
      <p>Spy Master code: <input v-model="spyMasterCode"></p>

      <div v-if="boardId">
        <Board :boardId="boardId" />
        <Tally :tallyRed="tallyRed" :tallyBlue="tallyBlue" />
      </div>
    </div>
  </div>
</template>

<script>

import Board from './components/Board.vue'
import Tally from './components/Tally.vue'

export default {
  name: 'App',
  components: {Board, Tally},
  data() {return{
    boardId: null,
    spyMasterCode: null,
    tallyRed: 0,
    tallyBlue: 0
  }},
  methods: {
    genCode: function() {
      var r = '', c = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
      for (var i = 0; i < 3; i++) {
        r += c.charAt(Math.floor(Math.random() * c.length))
      }
      this.spyMasterCode = r
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
