<template>
  <h1>New App</h1>
  <button v-on:click="startGame" v-bind:disabled="isPlaying">Start Game</button>

  <Block v-if="isPlaying" v-bind:delay="delay" v-on:end="endGame"/>

  <Results v-if="showResults" v-bind:score="score"/>
</template>

<script>
import Block from './components/Block';
import Results from './components/Results.vue';

export default {
  name: 'App',

  data () {
    return {
      isPlaying : false,
      delay: null,
      score: null,
      showResults: false
    }
  },

  components: {
    Block,
    Results
  },

  methods: {
    startGame () {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;

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

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
