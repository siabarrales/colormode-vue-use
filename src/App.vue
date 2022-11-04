<script setup>
import { useColorMode } from '@vueuse/core'
import HelloWorld from './components/HelloWorld.vue'
import IconSun from './components/IconSun.vue'
import IconMoon from './components/IconMoon.vue'

const colorMode = useColorMode()
const switchTheme = () => {
  colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark'
}
</script>

<template>
  <header class="header">
    <h4>Color Mode with VueUse</h4>
    <button @click="switchTheme" class="btn-theme">
      <IconSun v-if="colorMode === 'light'" /> 
      <IconMoon v-if="colorMode === 'dark'"/>
    </button>
  </header>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
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
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 50px;
}
.btn-theme{
  display: flex;
  align-items: center;
  font-size: 13px;
}
</style>
