<template>
  <div class="main">
    <h1>Ali's Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <!-- <p v-if="showResults">Reaction Time: {{ score }} ms</p> -->
    <ResultView :score="score" v-if="showResults" />
    <BlockView v-if="isPlaying" :delay="delay" @end="endGame" />
  </div>
</template>

<script>
import BlockView from "./components/BlockView.vue";
import ResultView from "./components/ResultView.vue";

export default {
  name: "App",
  components: { BlockView, ResultView },
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
      this.isPlaying = true;
      this.delay = 3000 + Math.random() * 5000;
      console.log(this.delay);
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
  color: #444;
  margin-top: 60px;
}
p {
  font-size: 25px;
}
button {
  background: rgb(17, 109, 78);
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
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
