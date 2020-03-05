<template>
  <div class="quotes-area">
    <quote-box v-for="(quote,index) in quotes" :key="index" :index="index">{{quote}}</quote-box>
  </div>
</template>

<script>
import quoteBox from "./Quote-Box.vue";
export default {
  props: ["quotes"],
  components: {
    quoteBox
  },
  
};
</script>

<style scoped>
.quotes-area {
  padding: 10px 0px;
  display: flex;
  flex-wrap: wrap;
}
</style>