<template>
  <div class=".container-xl ">
    <div id="heder" class="row">
      <MainHeder />
    </div>
    <section class="row">
      <div class="col">
        <rightAds />
      </div>
      <div id="containerCalculatur" class="col-6">
        <StartCalculator />
      </div>
      <div class="col">
        <leftAds />
      </div>
    </section>
  </div>
</template>

<script>
import MainHeder from "./components/MainHeder.vue";
import StartCalculator from "./components/startCalaulator.vue";
import rightAds from "./components/rightAds.vue";
import leftAds from "./components/leftAds.vue";

export default {
  name: "App",
  components: {
    MainHeder: MainHeder,
    StartCalculator: StartCalculator,
    rightAds: rightAds,
    leftAds: leftAds
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
  padding: 20px;
}

#app #containerCalculatur {
    margin: 0 10%;
    padding: 10px;
    background-color: #f0f0f0;
    border-radius: 10px;
    box-shadow: 0 0 10px #000;
  }

  #app section {
    margin-top: 50px;
  }
</style>
