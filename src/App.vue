<template>
  <div id="app">
    <h1>Ninja Reaction Timer</h1>
    <img src="https://icons.iconarchive.com/icons/webalys/kameleon.pics/256/Ninja-icon.png">
    <br><br>
    <button @click="start" :disabled="isPlaying" >Play &#9658;</button>
    <block v-if="isPlaying" :delay="delay" @stoppage="endGame" />
    <results v-if="showResults" :score="score" />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333;
  margin-top: 60px;
}

button {
  color: white;
  background: #0faf87;
  border-radius: 13px;
  border-color: white;
  cursor: pointer;
  font-size: 15px;
  
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>

<script>
import Block from './components/block.vue';
import block from './components/block.vue'
import results from './components/results.vue'


export default {
  name: "App",
  components: {Block, results},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000, 
      this.isPlaying = true
      this.showResults = false

    },

    endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false,
        this.showResults = true
    }
  },
};
</script>
