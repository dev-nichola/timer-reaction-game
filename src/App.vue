<template>
  <h1>Seberapa cepat kekuatan jarimu? Buktikan!</h1>
  <p>Tekan tombol dibawah untuk memulai permainan.</p>
  <button @click="startGame" :disabled="isPlaying">{{ buttonText }}</button>

  <p v-if="showScore">Waktu: {{ score ?? 0 }} ms</p>

  <Block v-if="isPlaying" :delay="delay" @gameOver="endGame" />
</template>

<script>
import Block from "./components/Block.vue";

export default {
  name: "App",

  data() {
    return {
      buttonText: "Mulai!",
      isPlaying: false,
      showScore: false,
      score: 0,
      delay: 0,
    };
  },

  methods: {
    startGame() {
      this.isPlaying = true;
      this.showScore = false;
      this.buttonText = "Sedang bermain...";
      this.delay = 500 + Math.floor(Math.random() * 2000);
    },
    endGame(score) {
      this.isPlaying = false;
      this.buttonText = "Mulai!";
      this.score = score;
      this.showScore = true;
    },
  },

  components: {
    Block,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

#app h1 {
  color: #101213;
}

#app p {
  color: #363c4097;
}
</style>
