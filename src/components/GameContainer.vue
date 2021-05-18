<template>
  <div class="game-container">
    <SceneDescription
      :currentDescription="{
        title: currentScene.title,
        description: currentScene.description
      }"
    />
    <SceneActions 
      :points="currentScene.points"
      @move-to-scene=""
      @show-examine-log="showLog($event)"
      @trigger-dialog="triggerDialog($event)"
    />
    <SceneLog
      :currentLog="currentLog"
      @clean-log="showLog({ title: '', lines: [] })"
    />
  </div>
</template>

<script>
import { scenes } from '../db/scenes.db';

import SceneDescription from './SceneDescription';
import SceneActions from './SceneActions';
import SceneLog from './SceneLog';

export default {
  name: 'GameContainer',
  components: {
    SceneDescription,
    SceneActions,
    SceneLog
  },
  data() {
    return {
      currentScene: {
        title: '',
        description: '',
        points: [],
      },
      inventory: [],
      currentLog: {
        title: '',
        lines: [],
      },
    };
  },
  methods: {
    showLog(logData) {
      this.currentLog.title = logData.title;
      this.currentLog.lines = [logData.description];
    },
    triggerDialog(dialogData) {
      this.currentLog = dialogData;
    }
  },
  mounted() {
    this.currentScene = scenes[0];
  }
}
</script>

<style scoped>
.game-container {
  display: grid;
  grid-template-columns: 80% 20%;
  grid-template-rows: 300px 150px;

  width: 60vw;
  border: 1px solid var(--color-primary);
  border-radius: 0.35em;
}

.game-container > :last-child {
  grid-column: 1 / span 2;
}

@media(max-width: 1000px) {
  .game-container {
    width: 90vw;
  }
}
</style>
