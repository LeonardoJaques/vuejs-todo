<template>
  <div>
    <v-list-item
      @click="store.commit('taskDone', task.id)"
      :class="{ 'blue light-5': task.done }"
    >
      <template v-slot:default>
        <v-list-item-action>
          <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title
            :class="{ 'text-decoration-line-through': task.done }"
          >
            {{ task.title }}
          </v-list-item-title>
        </v-list-item-content>
        <v-list-item-action v-if="task.dueDate">
          <v-list-item-action-text>
            <v-icon small>mdi-calendar</v-icon>
            {{ task.dueDate | niceDate }}
          </v-list-item-action-text>
        </v-list-item-action>

        <v-list-item-action>
          <task-menu :task="task" />
        </v-list-item-action>
      </template>
    </v-list-item>
    <v-divider></v-divider>
  </div>
</template>
<script>
import store from "@/store";
import TaskMenu from "./TaskMenu.vue";
import moment from "moment";

export default {
  name: "Task",
  filters: {
    niceDate(value) {
      return moment(value).format("MMM D");
    },
  },
  props: ["task"],
  components: {
    "task-menu": TaskMenu,
  },
  data: () => {
    return {
      store,
    };
  },
};
</script>
