<template>
  <div class="container">
    <div id="heder" class="row">
      <MainHeder />
    </div>
    <section class="row">
      <div class="col-3 d-none d-xl-flex flex-column">
        <rightAds />
      </div>
      <div id="containerCalculatur" class="col-xl-6">
        <StartCalculator />
      </div>
      <div class="col-3 d-none d-xl-flex flex-column ">
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
    leftAds: leftAds,
  },
  methods: {

  },
  compatConfig: { MODE: 3 }
};
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Serif+Hebrew:wght@100;200;300;400;500;600;700;800;900&display=swap');

#app {
  font-family: 'Noto Serif Hebrew', serif;
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 20px;
}

#app #containerCalculatur {
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0 0 10px #000;
}

@media (max-width: 1000px) {
  #app .adds {
    display: none;
  }

  #app #heder {
    display: block;
  }
}

#app section {
  margin-top: 50px;
}
</style>
