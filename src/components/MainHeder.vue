<template>
  <div class="header">
    <div class="logo">
      <img src="../assets/temp_logo.png" alt="logo" />
    </div>
    <div>
      <todayHebrewDate />
    </div>

    <div class="navigation">
      <button class="nav-button">בית</button>
      <button class="nav-button">מחשבון</button>
      <button class="nav-button">אודות</button>
      <button class="nav-button">צור קשר</button>
    </div>
  </div>
</template>
<script>
import todayHebrewDate from "./todayHebrewDate.vue";

export default {
  components: {
    todayHebrewDate: todayHebrewDate
  },
};
</script>
  
<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: row-reverse;
  background-color: #f0f0f0;
  padding: 10px;
}

img {
  width: 60px;
  height: 60px;
}

.navigation {
  display: flex;
}

.nav-button {
  background-color: transparent;
  border: none;
  margin: 0 10px;
  cursor: pointer;
  color: #000;
}

.nav-button:hover {
  color: #ff0000;
  /* צבע כאשר מעבירים את העכבר מעל הכפתור */
}
</style>
  