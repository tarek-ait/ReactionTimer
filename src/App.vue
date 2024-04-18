<template>
 <h1>Tarek reaction</h1>

 <button @click="start" :disabled="isPlaying">Play</button>
 <Block v-if="isPlaying" :delay="delay"  @end="endGame"/>
 <Result v-if="showResult" :score="score"/> <!-- we set the props here in the component tag-->
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
// starting game button 
export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
  return {
    isPlaying:false,
    delay:null,
    score:null,
    showResult:false,
  }
},
  methods: {
    start(){
      this.delay= 1000 + Math.random() * 2000 // giving a random amount of time
      console.log(this.delay)
      this.isPlaying = true
      this.showResult = false
  },
  endGame(reactionTime){ // the function automatically takes the value of the reactionTime as we set it on the second argument of the emit in the block component
    this.score=reactionTime
    this.showResult=true
    this.isPlaying = false
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
  color: #444;
  margin-top: 60px;
}
button {
    background: #0faf87;
    color: white;
    border: none;
    padding:8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor:not-allowed;
}
</style>
