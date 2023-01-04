<template>
  <div id="wrap">
    <div class="container">
      <div v-for="coins in coin" :key=coins.data>
        <p>{{coins.BTC}}</p>
        <p>비트코인</p>
      </div>
    </div>
    <div class="footer">
      <div class="footer_wrap">
        <div class="footer_text">
          <p>GitHub : https://github.com/pongja</p>
          <p>email : rlqjadl2222@naver.com</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import axios from 'axios'

const coin =ref([])
const bithumb = async () =>{
  try{
  await axios.get('https://api.bithumb.com/public/ticker/ALL_KRW', {
   headers: {
    accept: 'application/json'
    }
   })
  .then((res)=>{
    coin.value = res.data
    console.log(res)
  })
  }catch(error){
    console.log(error)
  }
}
bithumb()
</script>
<style scoped>
@import "~/assets/reset.css";
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}
#wrap {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  min-height: 100%;
  height: auto;
  padding: 200px 16px 160px 16px;
  flex:1;
}
.footer{
  width: 100%;
  height: 140px;
  display: flex;
  align-items: center;
  background: #5D70D7;
 }
 .footer .footer_wrap {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 16px;
}
.footer .footer_text {
  color: white;
  text-align: center;
  margin-top: 12px;
}
.footer .footer_text p {
  line-height: 1.6;
  font-size: 15px;
  margin-bottom: 0;
}
</style>