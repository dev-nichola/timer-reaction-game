<template>
  <div class="wobble" :style="loaderStyle"></div>
</template>
<script>
export default {
  name: "Loader",
  props: ["size", "speed", "color"],
  computed: {
    loaderStyle() {
      return {
        "--uib-size": this.size,
        "--uib-speed": this.speed,
        "--uib-color": this.color,
      };
    },
  },
};
</script>
<style scoped>
.wobble {
  --uib-size: 45px;
  --uib-speed: 0.9s;
  --uib-color: black;

  position: relative;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  height: var(--uib-size);
  width: var(--uib-size);
}

.wobble::before {
  content: "";
  height: 25%;
  width: 25%;
  border-radius: 50%;
  animation: wobble var(--uib-speed) ease-in-out infinite;
  transform: translate(0, calc(var(--uib-size) * -0.4));
  background-color: var(--uib-color);
}

@keyframes wobble {
  0%,
  100% {
    transform: translateX(0);
  }

  50% {
    transform: translateX(calc(var(--uib-size) * 0.75));
  }
}
</style>
