<template>
  <MainHeder />
  <StartCalculator />
</template>

<script>
import MainHeder from "./components/MainHeder.vue";
 import StartCalculator from "./components/startCalaulator.vue";

export default {
  name: "App",
  components: {
    MainHeder: MainHeder,
   StartCalculator: StartCalculator,
  },
  methods: {

  },
  compatConfig: { MODE: 3 }
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
</style>
