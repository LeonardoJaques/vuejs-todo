<template>
  <v-text-field
    @keyup.enter="addTask"
    v-model="newTaskTitle"
    outlined
    class="pa-3"
    label="Add task"
    hide-details
    clearable
  >
    <template v-slot:append>
      <v-icon @click="addTask" color="primary" :disabled="newTaskTitleInvalid">mdi-plus</v-icon>
    </template>
  </v-text-field>
</template>
<script>
import store from "@/store";
export default {
  data() {
    return {
      newTaskTitle: "",
      store,
    };
  },
  computed: {
    newTaskTitleInvalid() {
      return !this.newTaskTitle
    }
  },
  methods: {
    addTask() {
      if(!this.newTaskTitleInvalid)
      this.store.dispatch("addTask", this.newTaskTitle);
      this.newTaskTitle = "";
    },
  },
};
</script>
