<template lang="html">
  <div>
    <v-menu bottom left>
      <template v-slot:activator="{ on, attrs }">
        <v-btn color="primary" icon v-bind="attrs" v-on="on">
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
          @click="handleClick(index)"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    <dialog-delete
      v-if="dialogs.delete"
      :task="task"
      @close="dialogs.delete = false"
    />
    <dialog-edit
      v-if="dialogs.edit"
      :task="task"
      @close="dialogs.edit = false"
    />
    <dialog-due-date
      v-if="dialogs.dueDate"
      :task="task"
      @close="dialogs.dueDate = false"
    />
  </div>
</template>
<script>
import DialogsDelete from "./Dialogs/DialogsDelete.vue";
import DialogsEdit from "./Dialogs/DialogsEdit.vue";
import DialogDueDates from "./Dialogs/DialogDueDates.vue";
import store from "@/store";

export default {
  name: "TaskMenu",
  props: ["task"],
  data: () => ({
    dialogs: {
      delete: false,
      dueDate: false,
      edit: false,
    },
    store,
    items: [
      {
        title: "Edit",
        icon: "mdi-pencil",
        click() {
          this.dialogs.edit = true;
        },
      },
      {
        title: "Due Date",
        icon: "mdi-calendar",
        click() {
          this.dialogs.dueDate = true;
        },
      },
      {
        title: "Delete",
        icon: "mdi-delete",
        click() {
          this.dialogs.delete = true;
        },
      },
      {
        title: "Sort",
        icon: "mdi-drag-horizontal-variant",
        click() {
          this.store.commit("toggleSorting");
        },
      },
    ],
  }),
  methods: {
    handleClick(index) {
      this.items[index].click.call(this);
    },
  },
  components: {
    "dialog-edit": DialogsEdit,
    "dialog-delete": DialogsDelete,
    "dialog-due-date": DialogDueDates,
  },
};
</script>
