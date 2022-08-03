<template lang="html">
  <div class="text-subtitle-1 ml-4">{{ date }}</div>
</template>
<script>
import moment from "moment";
export default {
  data() {
    return {
      date: "",
    };
  },
  methods: {
    getDate() {
      this.date = moment().format("MMMM D, HH:mm:ss");
      setTimeout(this.getDate,1000);
    },
  },
  mounted() {
    this.getDate();
  },
};
</script>
