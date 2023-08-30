<template>
<div dir="ltr" id="TodayHebrewDate" style="margin-left: 20px;  "></div>
</template>

<!-- <script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  // compatConfig: { MODE: 3 }
}
</script> -->




<script>
export default {
  data: () => ({
   
  }),
  mounted() {
    let recaptchaScript = document.createElement('script')
    recaptchaScript.setAttribute('src', 'https://www.hebcal.com/etc/hdate-he-v2.js')
    document.head.appendChild(recaptchaScript)
  },
  methods: {
    
  }
}

</script>
<style scoped>

</style>
