<template>
  <Loader v-if="!showBlock" color="#363c4097" />
  <div class="block" v-if="showBlock" @click="pressed">
    <span>Tangkap aku!!!</span>
  </div>
</template>
<script>
import Loader from "./Loader.vue";

export default {
  data() {
    return {
      showBlock: false,
      interval: null,
      score: 0,
    };
  },
  props: ["delay"],
  emits: ["gameOver"],

  methods: {
    pressed() {
      clearInterval(this.interval);
      this.$emit("gameOver", this.score - this.delay);
    },
  },

  components: {
    Loader,
  },

  created() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },

  mounted() {
    this.interval = setInterval(() => {
      this.score += 10;
    }, 10);
  },
};
</script>
<style scoped>
.block {
  width: 200px;
  height: 200px;
  background-color: #8bd38b;
  color: black;

  border-radius: 50%;
  margin-top: 30px;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
}
</style>
