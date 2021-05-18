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
  --color-primary: #ffffff;
  --color-secondary: #333333;
}

body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  height: 100vh;
  margin: 0;
  box-sizing: border-box;
  background: var(--color-secondary);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--color-primary);
}
</style>
