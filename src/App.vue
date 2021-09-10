<template>
  <div @click="start" class="container">
    <i class="fas fa-bolt"></i>

    <h1 class="title">React as fast as you can!</h1>
  </div>
  <!-- <Footer /> -->
</template>

<script>
import Footer from './components/Footer.vue';
export default {
  name: 'App',
  components: { Footer },
  methods: {},
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Signika+Negative:wght@300&display=swap');

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
