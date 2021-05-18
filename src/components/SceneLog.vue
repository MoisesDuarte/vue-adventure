<template>
  <section class="scene-log">
      <p><strong>{{ currentLog.title }}</strong></p>
      <p>{{ currentLog.lines[logIndex] }}</p>
      <button v-if="isDialog">
        Next
      </button>
  </section>
</template>

<script>
export default {
  name: 'SceneLog',
  data() {
    return {
      logIndex: 0,
      isDialog: false,
    }
  },
  props: {
    currentLog: {
      type: Object,
    },
  },
}
</script>

<style scoped>
.scene-log {
  position: relative;
  border-top: 1px solid var(--color-black);
  padding: 0.5em;
}

.scene-log > button {
  border: 1px solid var(--color-black);
  border-radius: 2px;
  background: transparent;
  position: absolute;
  right: 6px;
  bottom: 0;
}

.scene-log > button:hover {
  background: var(--color-black);
  color: white;
  cursor: pointer;
}
</style>