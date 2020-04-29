<template>
  <div>
    <div>Board id: {{ bid }}, isSpyMaster: {{ isSpyMaster }}, spyMasterCode: {{ code }}</div>
    <table id="Board">
      <tr v-for="(column, i) in words" :key="i">
        <td v-for="v in boardWidth" :key="v" @click="cardClick(column[v])">{{ column[v] }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Board',
  props: {
    boardId: String,
    boardWidth: Number,
    isSpyMaster: Boolean,
    spyMasterCode: String
  },
  data: function() {return{
    words: [],
    bid: this.$props.boardId,
    code: this.$props.spyMasterCode
  }},
  mounted: function() {
    this.words = this.randomWords()
  },
  watch: {
    boardId: function(value, old) {
      this.bid = value
      this.words = this.randomWords()
    },
    spyMasterCode: function(value, old) {
      this.code = value
    }
  },
  methods: {
    randomWords: function() {
      // seed = boardId
      var taken = [],
          matrix = [],
          len = this.allWords.length

      for (var i = 0; i < this.boardWidth; i++) {
        var j = 0
        matrix[i] = []

        while (j <= this.boardWidth) {
          var r = Math.floor(Math.random() * len)
          var word = this.allWords[r]

          if (taken.indexOf(word) === -1) {
            taken.push(word)
            matrix[i][j] = word
            j++
          }
        }
      }

      return matrix
    },
    cardClick: function(value) {
      alert(value)
    }
  },
  computed: {
    allWords: function() {
      return [
        "africa","agent","air","alien","amazon","angel","antarctica","apple","arm","back","band","bank","bark","beach","belt","berlin","berry","board","bond","boom","bow","box","bug","canada","capital","cell","center","china","chocolate","circle","club","compound","copper","crash","cricket","cross","death","dice","dinosaur","doctor","dog","dress","dwarf","eagle","egypt","engine","england","europe","eye","fair","fall","fan","field","file","film","fish","flute","fly","forest","fork","france","gas","ghost","giant","glass","glove","gold","grass","greece","green","ham","head","himalaya","hole","hood","hook","human","horseshoe","hospital","hotel","ice","ice",
        "cream","india","iron","ivory","jam","jet","jupiter","kangaroo","ketchup","kid","king","kiwi","knife","knight","lab","lap","laser","lawyer","lead","lemon","limousine","leadlock","log","mammoth","maple","march","mass","mercury","millionaire","model","mole","moscow","mouth","mug","needle","net","new",
        "york","night","note","novel","nurse","nut","oil","olive","olympus","opera","orange","paper","park","part","paste","phoenix","piano","telescope","teacher","switch","swing","sub","stick","staff","stadium","sprint","spike","snowman","slip","shot","shadow","server","ruler","row","rose","root","rome","rock","robot","robin","revolution","rat","racket","queen","press","port","pilot","time","tooth","tower","truck","triangle","trip","turkey","undertaker","unicorn","vacuum","van","wake","wall","war","washer","washington","water","wave","well","whale","whip","worm","yard"
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #Board {
    font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
    width: 85%;
  }

  #Board td {
    text-align: center;
    border: 5px solid #ddd;
    width: 300px;
    height: 50px;
    padding: 10px;
  }

  #Board tr:nth-child(even) {
    background-color: #f2f2f2;
  }

  #Board tr:nth-child(odd) {
    background-color: white;
  }

  #Board td:hover {
    background-color: #ddd;
  }

</style>
