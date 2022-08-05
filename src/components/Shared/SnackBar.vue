<template lang="html">
  <v-snackbar v-model="store.state.snackbar.show">
    {{ store.state.snackbar.text }}

    <template v-slot:action="{ attrs }">
      <v-btn text v-bind="attrs" @click="store.commit('hideSnackbar')">
        Close
      </v-btn>
    </template>
  </v-snackbar>
</template>
<script>
import store from "@/store";

export default {
  name: "Snackbar",
  data: () => ({
    store,
  }),
};
</script>
<style>
  div.v-snack:not(.v-snak--absolute) {
    height: 100%;
  }
</style>
