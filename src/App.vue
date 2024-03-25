<template>
  <h1>React as first as you can.</h1>

  <button @click="start" :disabled="isPlaying">Play</button>

  <BlockComponent v-if="isPlaying" :delay="delay" @end="endGame"/>

  <ResultComponent v-if="showResult" :score="score"/>
</template>

<script>
import BlockComponent from './components/BlockComponent.vue'
import ResultComponent from './components/ResultComponent.vue'


export default {
  name: 'App',
  components: { BlockComponent, ResultComponent },

  data(){
      return{
        isPlaying: false,
        delay: null,
        score: null,
        showResult: false
      }
    },

    methods:{
      start(){
      this.delay = 2000 + Math.random() * 5000,
      this.isPlaying = true
      this.showResult = false
      },
      endGame(reactionTime){
        this.score = reactionTime
        this.isPlaying = false
        this.showResult = true
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
    color: #333;
    margin-top: 60px;
  }
  button{
    background: #058;
    color: white;
    border: none;
    padding: 8px 16px;
    margin: 10px;
    border-radius: 10px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
  }

  button[disabled]{
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
