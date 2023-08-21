<template>
 <!-- מסך ראשוני למחשבון -->
 <div id="Screen1" v-show="showScreen1">
      <h3>
        כמה דפים אני צריך לכתוב היום?
        <br />
        איך אני אמור לחשב כשיש לי חול המועד באמצע?
        <br />
        כמה תכלס אני מרוויח ביום על כתיבה?
        <br />
        רוצים לעשות סדר בכל הבלאגן?!
      </h3>
      <button @click="startCalculator">לחצו כאן להתחלת החישוב</button>
    </div>
    <div id="Screen2" v-show="showScreen2">
      <h1>בחר את סוג החישוב הרצוי</h1>
      <button @click="calculatorDate">לחישוב תאריך הגשה</button>
      <button @click="pagesCalculator">לחישוב כמות כתיבה</button>
    </div>
    <div v-show="showCalculatorDate">
    <CalDate />
    </div>
    <div v-show="showPagesCalculator">
    <pagesCalc />
    </div>

</template>

<script>
import CalDate from "./calculatorDate.vue";
import pagesCalc from "./pagesCalculator.vue";

export default {
  components: {
    CalDate: CalDate,
    pagesCalc:pagesCalc

  },
  data() {
      return {
      //הגדרת תצוגת מסכים
      showScreen1: true,
      showScreen2: false,
      showCalculatorDate: false,
      showPagesCalculator: false
      }},
  methods: {
    startCalculator() {
        this.showScreen1 = !this.showScreen1;
        this.showScreen2 = !this.showScreen2;
      },
      calculatorDate(){
        this.showScreen2 = false;
        this.showCalculatorDate = true;
      },
      pagesCalculator(){
        this.showScreen2 = false;
        this.showPagesCalculator = true;
      }
  }
}
</script>


<style>
</style>
