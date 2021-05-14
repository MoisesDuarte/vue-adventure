<template>
 <section class="scene-actions">
 <!-- TODO: Remove redundancy from template -->
    <ul v-if="isInitial">
      <li
        v-for="action in actions" 
        :key="action.id" 
        @click="onActionClick(action.trigger)">
        {{ action.name }}
      </li>
    </ul>
    <ul v-if="isMovement">
      <li 
        v-for="move in movePoints"
        :key="move.id"
        @click="onMovementClick(move)">
        {{ move.title }}
      </li>
      <li @click="goBackToActions()">
        Back
      </li>
    </ul>
    <ul v-if="isExamine">
      <li 
        v-for="examine in examinePoints"
        :key="examine.id"
        @click="onExamineClick(examine)">
        {{ examine.title }}
      </li>
      <li @click="goBackToActions()">
        Back
      </li>
    </ul>
  </section>
</template>

<script>
// TODO: Remove redundancy from code
export default {
  name: 'SceneActions',
  props: {
    points: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      actions: [],
      movePoints: this.points.move,
      examinePoints: this.points.examine,
      talkPoins: this.points.talk,
      interactPoints: this.points.interact,
      isInitial: true,
      isMovement: false,
      isExamine: false,
      isTalk: false,
      isInteract: false,
      isInventory: false,
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
      this.isInitial = false;
      this.isMovement = true;
    },
    onMovementClick(movement) {

    },
    setExaminePoints() {
      this.isInitial = false;
      this.isExamine = true;
    },
    onExamineClick(examination) {
      const { title, description } = examination;
      this.$emit('show-examine-log', { title, description });
    },
    setTalkPoints() {
      console.info('setTalkPoints');
    },
    onTalkClick(talk) {

    },
    setInteractPoints() {
      console.info('setInteractPoints');
    },
    onInteractClick(interaction) {
      
    },
    setInventory() {
      console.info('setInventory');
    },
    goBackToActions() {
      this.$emit('show-examine-log', { title: '', description: '' });
      this.isInitial = true;
      this.isMovement = false;
      this.isExamine = false;
      this.isTalk = false;
      this.isInteract = false;
      this.isInventory = false;
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