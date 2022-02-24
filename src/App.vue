<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <Block v-if="isPlaying" :delay="delay" @sendReactionTime="endGame" />
  <!-- <p v-if="showResults">Your reaction time: {{ score }} ms</p> -->
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      // console.log(this.delay);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #273e49;
  margin-top: 6rem;
}
button {
  background: #a1b57d;
  color: #fff;
  border: none;
  padding: 0.8rem 1.6rem;
  border-radius: 8px;
  font-size: 1.6rem;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 3rem;
  font-weight: 500;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
