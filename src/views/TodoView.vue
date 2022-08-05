<template lang="html">
  <div class="home">
    <list-tasks v-if="store.state.tasks.length" />
    <no-task v-else />
    <button-done-sorting v-if="store.state.sorting" />
  </div>
</template>

<script>
import store from "@/store";

import ListTasks from "@/components/Todo/ListTasks.vue";
import NoTasks from "@/components/Todo/NoTasks.vue";
import ButtonDoneSorting from "@/components/Todo/ButtonDoneSortring.vue";

export default {
  name: "Home",
  data: () => {
    return {
      store,
    };
  },
  components: {
    "list-tasks": ListTasks,
    "no-task": NoTasks,
    "button-done-sorting": ButtonDoneSorting,
  },
};
</script>
