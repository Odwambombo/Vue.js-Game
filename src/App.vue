<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="toggle" :disabled="isVisible">Play</button>
  <MakerUser v-if="isVisible" :delay="delay" @close='result'/>
  <FinalResults :score="score" :finalR="finalR" v-if="showFinalResult"/>
</template>

<script>
import MakerUser from './components/MakerUser.vue'
import FinalResults from './components/FinalResults.vue'

export default {
  name: 'App',
  components: { MakerUser, FinalResults},
  data() {
    return{
      isVisible: false,
      delay: null,
      score: null,
      finalR: null,
      showFinalResult: false
    }
  },
  methods: {
    toggle(){
      this.delay = 2000 + Math.random() * 5000
      this.isVisible = true,
      this.showFinalResult = false
    },
    result(res){
      this.score = res,
      this.isVisible = false
      this.showFinalResult = true

      if(this.score < 250){
        this.finalR = 'Ninja Reflexes'
      }
      else if (this.score < 450){
        this.finalR = 'Good Refexes'
      }
      else{
        this.finalR = 'Snail Pace...'
      }
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
  background-color: #E1F5FE;
}
body{
  background-color: #E1F5FE;
}
button{
  background: #4DB6AC;
  border: solid #4DB6AC;
  border-radius: 3px;
  color: #fff;
  padding: 5px;
  font-weight:bolder;
  cursor: pointer;
}
button[disabled] {
  cursor: not-allowed;
  opacity: 0.2;
}


</style>
