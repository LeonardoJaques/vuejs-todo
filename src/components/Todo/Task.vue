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
            >{{ task.title }}</v-list-item-title
          >
        </v-list-item-content>
        <v-list-item-action>
          <v-btn @click.stop="store.dispatch('deleteTask', task.id)" icon>
            <v-icon color="primary lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
      </template>
    </v-list-item>
    <v-divider></v-divider>
  </div>
</template>
<script>
import store from "@/store";

export default {
  name: "Task",
  props: ["task"],
  data: () => {
    return {
      store,
     };
  },
};
</script>
