<template lang="html">
  <v-list flat class="pt-0">
    <task
    v-for="task in store.getters.taskFiltered"
    :key="task.id"
    :task="task" />
  </v-list>
</template>
<script lang="js">

import store from "@/store";
import Task from "./Task.vue";
export default {
  name: "ListTasks",
  components: {
    "task": Task
  },
  data: () => {
    return { store }
  }
};
</script>
