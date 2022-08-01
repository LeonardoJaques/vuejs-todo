<template lang="html">
  <v-dialog
    ref="dialog"
    :value="true"
    :return-value.sync="date"
    persistent
    width="290px"
  >
    <v-date-picker v-model="date" scrollable>
      <v-spacer></v-spacer>
      <v-btn text color="primary" @click="$emit('close')"> Cancel </v-btn>
      <v-btn text color="primary" @click="saveTask"> OK </v-btn>
    </v-date-picker>
  </v-dialog>
</template>
<script>
import store from "@/store";

export default {
  name: "DialogDueDate",
  props: ["task"],
  data() {
    return {
      date: null,
      store
    };
  },
  mounted() {
    if (this.task.dueDate) {
      this.date = this.task.dueDate;
    }
  },
  methods: {
    saveTask() {
      let payLoad = {
        id: this.task.id,
        dueDate: this.date,
      };
      this.store.dispatch("updateTaskDueDate", payLoad);
      this.$emit("close")
    },
  },
};
</script>
