<template lang="">
  <div @click="missClick" class="block waiting" v-if="showWaiting">
    <i class="fas fa-ellipsis-h"></i>
    <h1>Wait for green...</h1>
  </div>
  <div class="block click" v-if="showClick" @click="stopTimer">
    <i class="fas fa-angle-double-down"></i>
    <h1>Click!</h1>
  </div>
  <div v-if="showResults" class="block results" @click="retryGame">
    <i class="fas fa-clock"></i>
    <h1 class="rtime">{{ reactionTime }} ms</h1>
    <h2>Click to try again!</h2>
    <h3>{{ reactionTime < 200 ? "Damn, he's fast!" : null }}</h3>
  </div>
  <div @click="tryAgain" class="block missclick" v-if="showMissClick">
    <i class="fas fa-exclamation-circle"></i>
    <h1>Too soon!</h1>
    <h2>Click to try again!</h2>
  </div>
</template>
<script>
export default {
  props: ['delay'],
  data() {
    return {
      rank: null,
      showResults: false,
      showClick: false,
      showWaiting: true,
      showMissClick: false,
      timer: null,
      reactionTime: 0,
      timeout: null,
    };
  },

  mounted() {
    this.timeout = setTimeout(() => {
      this.showWaiting = false;
      this.showClick = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    tryAgain() {
      this.showMissClick = false;
      this.showWaiting = true;
      setTimeout(() => {
        this.showWaiting = false;
        this.showClick = true;
        this.startTimer();
      }, this.delay);
    },

    missClick() {
      this.showMissClick = true;
      this.showWaiting = false;
      clearTimeout(this.timeout);
    },

    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.showClick = false;
      this.showResults = true;
    },
    retryGame() {
      this.$emit('retry', this.showResults);
    },
  },
};
</script>
<style scoped>
.block {
  height: 100vh;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.waiting {
  background-color: #e85600;
}
.click {
  background-color: #32b643;
}

.results {
  background-color: #fc919b;
}
.missclick {
  background-color: #0089bd;
}

h1 {
  color: white;
  font-size: 50px;
}

h3 {
  font-style: italic;
}

.rtime {
  font-size: 70px;
  font-weight: bold;
}
</style>
