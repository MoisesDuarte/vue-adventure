<template>
  <section class="scene-log">
      <p><strong>{{ currentLog.title }}</strong></p>
      <p>{{ currentLog.lines[logIndex] }}</p>
      <button 
        v-if="currentLog.lines.length > 1" 
        @click="onNextClick">
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
    }
  },
  methods: {
    onNextClick() {
      this.logIndex = this.logIndex + 1 < this.currentLog.lines.length ? this.logIndex + 1 : 0;
      if (this.logIndex === 0) this.$emit('clean-log');
    },
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
  border: none;
  border-radius: 2px;
  background: transparent;
  position: absolute;
  right: 6px;
  bottom: -8px;
}

.scene-log > button:hover {
  background: var(--color-black);
  color: white;
  cursor: pointer;
}
</style>