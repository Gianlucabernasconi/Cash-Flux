<script setup>
import SplashScreen from './components/SplashScreen.vue'
import { defineAsyncComponent } from 'vue'

const Home = defineAsyncComponent(() => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = true
      if (success) {
        resolve(import('./components/Home.vue'))
      } else {
        reject(new Error('Error al cargar el componente Home.vue'))
      }
    }, 2500)
  })
})
</script>

<template>
  <Suspense>
    <template #default>
      <Home></Home>
    </template>
    <template #fallback>
      <splash-screen></splash-screen>
    </template>
  </Suspense>
</template>

<style>
html,
body,
#app {
  min-height: 100vh;
  margin: 0;
  font-family: 'Genos', sans-serif;
}
</style>
