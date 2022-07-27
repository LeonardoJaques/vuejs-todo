<template lang="html">
  <v-dialog :value="true" persistent max-width="290">
    <v-card>
      <v-card-title class="text-h5"> Edit task </v-card-title>
      <v-card-text>
        Edit the title of this task:
        <v-text-field v-model="taskTitle" @keyup.enter="saveTask" />
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn text @click="$emit('close')"> Cancel </v-btn>
        <v-btn
          color="red darken-1"
          text
          @click="saveTask"
          :disabled="taskTitleInvalid"
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>
import store from "@/store";
export default {
  name: "DialogDelete",
  props: ["task"],
  computed: {
    taskTitleInvalid() {
      return !this.taskTitle || this.taskTitle === this.task.title;
    },
  },
  methods: {
    saveTask() {
      if (!this.taskTitleInvalid) {
        let payLoad = {
          id: this.task.id,
          title: this.taskTitle,
        };
        store.dispatch("updateTaskTitle", payLoad);
        this.$emit("close");
      }
    },
  },
  mounted() {
    this.taskTitle = this.task.title;
  },
  data() {
    return { store, taskTitle: null };
  },
};
</script>
