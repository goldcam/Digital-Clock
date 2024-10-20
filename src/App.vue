<template>
  <div id="app">
    <Clock />
  </div>
</template>

<script>
import Clock from './components/Clock.vue'

export default {
  name: 'App',
  components: {
    Clock
  }
}
</script>

<style>

html, body {
  width: 100%;
  height: 100%;
}
body {
  margin: 0;
  padding: 0;
  font-family: 'Orbitron', sans-serif;
  font-weight: 700;
  background: #222222;
  color: #afeeee;
  display: flex;
  align-items: center;
  justify-content: center;
}
#app {
  width: 100%;
}
</style>
