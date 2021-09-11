<template>
  <div v-if="!isPlaying" @click="start" class="container">
    <i class="fas fa-bolt"></i>
    <h1 class="title">React as fast as you can!</h1>
  </div>
  <Game @retry="retry" v-if="isPlaying" :delay="delay" />

  <!-- <Footer /> -->
</template>

<script>
import Footer from './components/Footer.vue';
import Game from './components/Game.vue';
export default {
  name: 'App',
  components: { Footer, Game },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 2000;
      this.isPlaying = true;
      console.log(this.isPlaying);
    },
    retry(isPlaying) {
      this.isPlaying = !isPlaying;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Signika+Negative:wght@300&display=swap');

#app {
  font-family: 'Signika Negative', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}

i {
  color: white;
  font-size: 100px;
  margin-bottom: 30px;
}

.title {
  padding: 20px;
  background-color: #fc919b;
  font-family: 'Signika Negative', sans-serif;
  font-size: 50px;
}

.container {
  height: 100vh;
  cursor: pointer;
  background-color: #0089bd;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>
