<template>
  <section class="scene-log">
      <p><strong>{{ log.title }}</strong></p>
      <p>{{ log.description }}</p>
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
  data() {
    return {
      log: this.currentLog,
    };
  },
  computed: {
    isLogEmpty: function () {
      return Object.keys(this.log).length === 0 && this.log.constructor === Object
    },
  },
}
</script>

<style scoped>
.scene-log {
  border-top: 1px solid var(--color-black);
  padding: 0.5em;
}

.scene-log {

}
</style>