<template>
  <div class="game-container">
    <SceneDescription />
    <SceneActions :points="currentScene.points" />
    <SceneLog />
  </div>
</template>

<script>
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
        title: 'Anathema Purification Chamber',
        description: 'Lorem ipsum ent dolor sit amet',
        points: {
          move: [
            {
              id: 0,
              title: 'Flow Control Center',
              slug: 'flow_control_center'
            }
          ],
          examine: [
            {
              id: 0,
              title: 'Flow Monitoring Device',
              slug: 'flow_monitoring_device',
              description: 'Device used in conscience mapping and anathema recognition',
            },
            {
              id: 1,
              title: 'Crystal Line Emitter',
              description: 'Laser cutting device powered by a red crystal'
            },
          ],
          talk: [
            {
              id: 0,
              title: 'Senior Crimson Wanderer',
              lines: [
                'It\'s been a while since someone visited the anathema chamber.',
                'For good reason. It isn\'t a very pleasant place for the weak minded.',
                'Even the strong-minded fail to reason with it sometimes.',
                'Take yout time, though. It\'s a interesting place for the spiritually minded such as yourself.'
              ]
            }
          ],
          interact: [],
        },
      },
      inventory: [],
    };
  },
}
</script>

<style scoped>
.game-container {
  display: grid;
  grid-template-columns: 80% 20%;
}

.game-container > :last-child {
  grid-column: 1 / span 2;
}
</style>
