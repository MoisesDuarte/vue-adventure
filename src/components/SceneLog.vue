<template>
  <section class="scene-log">
      <p><strong>{{ currentLog.title }}</strong></p>
      <p>{{ currentLog.description }}</p>
  </section>
</template>

<script>
export default {
  name: 'SceneLog',
  props: {
    currentLog: {
      type: Object,
    }
  },
}
</script>

<style scoped>
.scene-log {
  border-top: 1px solid var(--color-black);
  padding: 0.5em;
}
</style>