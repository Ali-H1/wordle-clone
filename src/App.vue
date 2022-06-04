<template>
  <div class="">
    <div class="row justify-content-center title"><h2> Wordle Clone:)</h2></div>
    <div class="row justify-content-center">
      <div class="col-2"></div>
      <wordcontainer class="col-11 col-sm-5 wordcontainer"/>
      <div class="col-2"></div>
      <Keyboard class="keyboard col-11 col-sm-6" />
    </div>
  </div>
</template>

<script>
import Keyboard from "./components/Keyboard.vue";
import wordcontainer from "./components/wordcontainer.vue";

export default {
  name: "App",
  components: {
    Keyboard,
    wordcontainer,
  },
};
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
.wordcontainer {
  margin-bottom: 80px;
}
.title{
  margin-bottom: 20px;
}
</style>
