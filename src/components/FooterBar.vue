<template>
  <div class="foot-container">
    <div class="footer">
      Powered by {{ author }} 
    </div>
  </div>
</template>
<script setup>

import {ref} from "vue";

const title = ref(process.env.VUE_APP_TITLE)
const version = ref(process.env.VUE_APP_VERSION)
const author = ref('小飞侠AI')
const beian = ref('')
</script>

<style scoped lang="stylus">
.foot-container {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  display flex;
  justify-content center
  color:#333;
  .footer {
    max-width 400px;
    text-align center;
    font-size 14px;
    padding 20px;
    width 100%
  }
}

</style>