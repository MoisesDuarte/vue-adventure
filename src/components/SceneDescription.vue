<template>
<!-- TODO: Rather than a description, maybe an image would be better -->
  <section class="scene-description">
    <p><strong>{{ currentDescription.title }}</strong></p>
    <p>{{ currentDescription.description }}</p>
  </section>
</template>

<script>
export default {
  name: 'SceneDescription',
  props: {
    currentDescription: {
      type: Object,
    }
  }
}
</script>

<style scoped>
.scene-description {
  padding: 0.5em;
}
</style>