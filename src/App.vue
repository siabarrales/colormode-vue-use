<script setup>
import { onMounted } from 'vue'
import { useColorMode } from '@vueuse/core'
import IconSun from './components/IconSun.vue'
import IconMoon from './components/IconMoon.vue'
import IconCafe from './components/IconCafe.vue'

const colorMode = useColorMode({
  modes: {
    cafe: 'cafe'
  }
})

const switchTheme = () => {
  if(colorMode.value === 'dark'){
    colorMode.value = 'cafe'
  } else if(colorMode.value === 'cafe') {
    colorMode.value = 'light'
  } else {
    colorMode.value = 'dark'
  }
}

const capitalize = (word) => {
  return word.charAt(0).toUpperCase() + word.slice(1);
}

</script>

<template>
  <header class="header">
    <h4>Color Mode with VueUse</h4>
    <button @click="switchTheme" class="btn-theme">
      <div class="btn-info" v-if="colorMode === 'light'">
        <IconSun /> <span>{{capitalize(colorMode)}}</span>
      </div>
      <div class="btn-info" v-else-if="colorMode === 'dark'">
        <IconMoon /> <span>{{capitalize(colorMode)}}</span>
      </div>
      <div class="btn-info" v-else>
        <IconCafe /> <span>{{capitalize(colorMode)}}</span>
      </div>    
    </button>
  </header>
  <div class="container">
    <h1 v-if="colorMode === 'light'">Works</h1>
    <h1 v-else-if="colorMode === 'dark'">With</h1>
    <h1 v-else>LocalStorage :)</h1>
  </div>
</template>

<style>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.light{
  background-color: #fff;
  color: #242424;
}
.cafe{
  filter: sepia(.9) hue-rotate(315deg) brightness(.9)
}
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 70px;
}
.btn-theme{
  display: flex;
  align-items: center;
  font-size: 15px;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.btn-info{
  display: flex;
  align-items: center;
}
span {
  padding-left: 10px;
}
</style>
