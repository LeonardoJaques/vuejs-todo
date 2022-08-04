<template lang="html">
  <v-list flat class="pt-0">
    <draggable v-model="tasks" handle=".handle" item-key="task.id">
      <task v-for="task in tasks" :key="task.id" :task="task" />
    </draggable>
  </v-list>
</template>
<script lang="js">

import store from "@/store";
import Task from "./Task.vue";
import draggable from 'vuedraggable'

export default {
  computed: {
    tasks: {
        get() {
            return this.store.getters.taskFiltered
        },
        set(value) {
            this.store.dispatch('setTasks', value)
        }
    }
  },
  components: {
    "task": Task,
        draggable
  },
  data: () => {
    return { store }
  },

};
</script>
