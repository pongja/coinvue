<template>
  <div class="header">
    <div class="header_wrap">
      <p
        class="logo_p"
        style="cursor:pointer;"
        @click="dashboard()">
        CoinVue
      </p>
      <ul class="gnb">
        <li>
          <router-link
            to="/">
            현재가 전체 정보
          </router-link>
        </li>
         <li>
          <router-link
            to="/">
            호가 전체 정보
          </router-link>
        </li>
        <li>
          <router-link to="/">
            빗썸
          </router-link>
        </li>
        <li>
          <router-link to="/">
            업비트
          </router-link>
        </li>
      </ul>
      <button
        :class="{'menu_btn on' : openmenu }"
        class="menu_btn"
        @click="openmenu = !openmenu">
        <!-- <span
          class="line"
          :class="{ 'menu_btn.on line' : openmenu}"></span> -->
      </button>
    </div>
    <nav
      :class="{ 'mo_gnb on' : openmenu }"
      class="mo_gnb">
      <ul>
        <li>
          <router-link
            to="/"
            class="on">
            현재가 전체 정보
          </router-link>
        </li>
        <li>
          <router-link to="/itempage">
            호가 전체 정보
          </router-link>
        </li>
      </ul>
    </nav>
  </div> 
  <div
    class="sidebar-overlay"
    :class="{ 'sidebar-overlay on' : openmenu }"></div>
</template>
<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const dashboard = () =>{
  router.push({
    name: 'home'
  })
}
const openmenu = ref(false)
</script>
<style scoped>
@import "~/assets/header.css";
@import "~/assets/reset.css";
</style>
