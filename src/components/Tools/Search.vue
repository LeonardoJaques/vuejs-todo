<template lang="html">
  <v-text-field
  v-model="search"
    @focus="searchClose = false"
    @blur="searchClose = true"
    class="expanding-search mt-1"
    :class="{'closed': searchClose && !search}"
    placeholder="Search"
    filled
    dense
    clearable
    prepend-inner-icon="mdi-magnify"
  ></v-text-field>
</template>
<script>
export default {
  name: "Search",
  data() {
    return {
      search: null,
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
