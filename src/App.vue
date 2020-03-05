<template>
  <div class="container">
    <quote-heading :totalQuotes.sync="totalQuotes"></quote-heading>
    <quote-adding :totalQuotes.sync="totalQuotes"></quote-adding>
    <quote-grid :quotes="quotes"></quote-grid>
    <quote-footer></quote-footer>
  </div>
</template>

<script>
import quoteHeading from "./Component/Quote-Added-Component.vue";
import quoteAdding from "./Component/Quote-Adding-Component.vue";
import quoteGrid from "./Component/Quote-Grid-Component.vue";
import quoteFooter from "./Component/Quote-Footer.vue";
import { eventBus } from "./main";
export default {
  components: {
    quoteHeading,
    quoteAdding,
    quoteGrid,
    quoteFooter
  },
  data() {
    return {
      quotes: [],
      totalQuotes: 0
    };
  },
  created() {
    eventBus.$on("quoteArrayEvent", data => {
      this.quotes = data;
    });
    
      console.log(this.totalQuotes)
  }
};
</script>

<style>
</style>







