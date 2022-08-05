<template>
  <v-text-field
    @keyup.enter="addTask"
    v-model="newTaskTitle"
    outlined
    class="field-add-task pa-3"
    placeholder="Add task"
    hide-details
    clearable
  >
    <template v-slot:append>
      <v-icon @click="addTask" :disabled="newTaskTitleInvalid">mdi-plus</v-icon>
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
      return !this.newTaskTitle;
    },
  },
  methods: {
    addTask() {
      if (!this.newTaskTitleInvalid)
        this.store.dispatch("addTask", this.newTaskTitle);
      this.newTaskTitle = "";
    },
  },
};
</script>
<style lang="sass">
.field-add-task.v-input--is-focused
  .v-input__slot
     background-color: rgba(31, 94, 129, 0.5)
</style>
