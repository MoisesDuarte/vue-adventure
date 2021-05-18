<template>
<!-- TODO: Rather than a description, maybe an image would be better -->
  <section class="scene-description">
    <h1>{{ currentDescription.title }}</h1>
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
  color: var(--color-primary);
  padding: 1.5em;
}

.scene-description > h1, p {
  margin: 0;
  margin-bottom: 0.25em
}
</style>