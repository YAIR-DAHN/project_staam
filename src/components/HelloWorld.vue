<template>
 <div dir="ltr" id="TodayHebrewDate" style="margin-left: 20px;  ">
    <script type="application/javascript" defer src = "https://www.hebcal.com/etc/hdate-he-v2.js"></script>
    <!-- <script>
      var d = new Date();
      var options = { year: 'numeric', month: 'long', day: 'numeric' };
      document.getElementById("TodayHebrewDate").innerHTML = d.toLocaleDateString('he-IL', options);
    </script> -->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  // compatConfig: { MODE: 3 }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
