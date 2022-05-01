<template>
  <h1>DevMaxwel Reaction Timer</h1>
  <button @click="startGame" :disabled="isStart">Play Game</button>
  <Block v-if="isStart" :delay="delay" @stop="endGame"/>
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  data() {
    return {
      isStart: false,
      delay: null,
      score:null,
      showResults:false,
    };
  },
  components: { Block, Results },
  methods: {
    startGame() {
      this.delay = 2000 + Math.floor(Math.random() * 5000);
      this.isStart = true;
      console.log(this.delay);
      this.showResults=false
    },
    endGame(reactionTime){
        this.score = reactionTime;
        this.isStart =false
        this.showResults = true
    }
  },
};
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
