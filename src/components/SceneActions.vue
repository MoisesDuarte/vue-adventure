<template>
 <section class="scene-actions">
 <!-- TODO: Remove redundancy from template -->
    <ul v-if="isInitial">
      <li
        v-for="action in actions" 
        :key="action.id" 
        @click="onActionClick(action.slug)">
        {{ action.name }}
      </li>
    </ul>
    <ul v-if="!isInitial">
      <li 
        v-for="action in subActions"
        :key="action.id"
        @click="onSubActionClick(action)">
        {{ action.title }}
      </li>
      <li @click="goBackToActions()">
        Back
      </li>
    </ul>
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
      subActions: [],
      subActionType: '',
      showSubActions: false,
      isInitial: true,
    };
  },
  methods: {
    setInitialActions() {
      this.actions = [
        { id: 0, name: 'Move', slug: 'move' },
        { id: 1, name: 'Examine', slug: 'examine' },
        { id: 2, name: 'Talk', slug: 'talk' },
        { id: 3, name: 'Interact', slug: 'interact' },
        { id: 4, name: 'Inventory', slug: 'inventory' },
      ]
    },
    onActionClick(type) {
      this.subActionType = type;
      this.subActions = this.points[type];
      this.isInitial = false;
    },
    onSubActionClick(action) {
      const actionTriggers = {
        move: () => {
          const { slug } = action;
          this.$emit('move-to-scene', slug);
        },
        examine: () => {
          const { title, description } = action;
          this.$emit('show-examine-log', { title, description });
        },
        talk: () => {
          const { title, lines } = action;
          this.$emit('trigger-dialog', { title, lines });
        },
        interact: () => {
          //
        },
        inventory: () => {
          //
        }
      };

      actionTriggers[this.subActionType]();
    },
    goBackToActions() {
      this.$emit('show-examine-log', { title: '', description: '' });
      this.subActionType = '';
      this.isInitial = true;
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