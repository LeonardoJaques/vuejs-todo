<template>
  <v-btn
    @click="store.commit('toggleSorting')"
    class="button-done-sorting"
    color="primary"
  >
    Done sorting
  </v-btn>
</template>
<script>
import store from "@/store";

export default {
  data() {
    return {
      store,
    };
  },
};
</script>
<style lang="sass">
.button-done-sorting
  position: fixed
  bottom: 20px
  left: 50%
  transform: translateX(-50%)
</style>
