<template lang="html">
  <div class="home">
    <field-add-task />
    <list-tasks v-if="store.state.tasks.length" />
    <no-task v-else />
    <button-done-sorting v-if="store.state.sorting"/>
  </div>
</template>

<script>
import store from "@/store";
import FieldAddTask from "@/components/Todo/FieldAddTask.vue";
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
    "field-add-task": FieldAddTask,
    "list-tasks": ListTasks,
    "no-task": NoTasks,
    "button-done-sorting": ButtonDoneSorting,
  },
};
</script>


