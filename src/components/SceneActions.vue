<template>
 <section class="scene-actions">
    <ul>
      <li
        v-for="action in actions" 
        :key="action.id" 
        @click="onActionClick(action.trigger)">
        {{ action.name }}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'SceneActions',
  data() {
    return {
      actions: [],
    };
  },
  methods: {
    setInitialActions() {
      this.actions = [
        { id: 0, name: 'Move', trigger: 'move' },
        { id: 1, name: 'Examine', trigger: 'examine' },
        { id: 2, name: 'Talk', trigger: 'talk' },
        { id: 3, name: 'Interact', trigger: 'interact' },
        { id: 4, name: 'Inventory', trigger: 'inventory' },
      ]
    },
    onActionClick(trigger) {
      const triggerFunctions = {
        move: () => { this.setMovementPoints() },
        examine: () => { this.setExaminePoints() },
        talk: () => { this.setTalkPoints() },
        interact: () => { this.setInteractPoints() },
        inventory: () => { this.setInventory() }
      }

      triggerFunctions[trigger]();
    },
    setMovementPoints() {
      console.info('setMovementPoints');
    },
    setExaminePoints() {
      console.info('setExaminePoints');
    },
    setTalkPoints() {
      console.info('setTalkPoints');
    },
    setInteractPoints() {
      console.info('setInteractPoints');
    },
    setInventory() {
      console.info('setInventory');
    }
  },
  created() {
    this.setInitialActions();
  },
}
</script>

<style scoped>
.scene-actions {
  border-left: 1px solid var(--color-black);
}

.scene-actions > ul {
  list-style: none;
  margin: 0;
  padding: 0.5em;
}

.scene-actions > ul > li {
  margin-bottom: 0.25em;
}

.scene-actions > ul > li:hover {
  background: var(--color-black);
  color: white;
  cursor: pointer;
}
</style>