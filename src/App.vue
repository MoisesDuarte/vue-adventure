<template>
  <div id="app">
    <GameContainer />
  </div>
</template>

<script>
import GameContainer from './components/GameContainer.vue'

export default {
  name: 'App',
  components: {
    GameContainer
  }
}
</script>

<style>
:root {
  --color-black: #2c3e50;
  --color-white: #ffffff;
}

html {
  box-sizing: border-box;
}

#app {
  height: 95vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--color-black);
}
</style>
