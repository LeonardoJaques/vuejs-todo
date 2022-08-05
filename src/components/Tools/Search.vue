<template lang="html">
  <v-text-field
    :value="store.state.search"
    @input="store.commit('setSearch', $event)"
    @focus="searchClose = false"
    @blur="searchClose = true"
    class="expanding-search mt-1"
    :class="{'closed': searchClose && !store.state.search}"
    placeholder="Search"
    filled
    dense
    clearable
    prepend-inner-icon="mdi-magnify"
    :disabled="store.state.sorting"
  ></v-text-field>
</template>
<script>
import store from '@/store';

export default {
  name: "Search",
  data() {
    return {
      store,
      searchClose: true,
    };
  },
};
</script>
<style lang="sass">
.expanding-search
  transition: max-width 0.3s
  .v-input__slot
    cursor: pointer !important
    &:before, &:after
      border-color: transparent !important
  &.closed
    max-width: 2.8125rem
    .v-input__slot
      background: transparent !important
</style>
