<template>
  <v-text-field
    @click:append="addTask"
    @keyup.enter="addTask"
    v-model="newTaskTitle"
    outlined
    class="pa-3"
    label="Add task"
    append-icon="mdi-plus"
    hide-details
    clearable
  ></v-text-field>
</template>
<script>
import store from "@/store";
export default {
  data() {
    return {
      newTaskTitle: "",
      store
    };
  },
  methods: {
    addTask() {
      this.store.dispatch("addTask", this.newTaskTitle);
      this.newTaskTitle = "";
    },
  },
};
</script>

