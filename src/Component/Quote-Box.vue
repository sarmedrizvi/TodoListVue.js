<template>
  <div class="quote" @click="deleteQuote">
    <span>
      <slot></slot>
    </span>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  data() {
    return {
      quotes: [],
      totalQuotes: Number
    };
  },
  props: ["index"],
  methods: {
    deleteQuote() {
      // console.log(this.totalQuotes);
      this.quotes.splice(this.index, 1);
      eventBus.$emit("quoteArrayEvent", this.quotes);
      this.totalQuotes--;
      eventBus.$emit("totalQuotes", this.totalQuotes);
    }
  },
  created() {
    eventBus.$on("quoteArrayEvent", data => {
      this.quotes = data;
    });
    eventBus.$on("totalQuotes", data => {
      this.totalQuotes = data;
    });
  }
};
</script>

<style scoped>
span {
  color: rgb(82, 82, 82);
  font-family: "Arizonia", cursive;
  font-size: 24px;
  color: #6e6e6e;
  /* min-width: 2px; */
  word-break: break-all;
  height: 100%;
}
.quote {
  border-radius: 4px;
  width: 20%;
  height: 80px;
  padding: 10px;
  border: 0.5px solid rgb(202, 199, 199);
  transition: background 0.2s ease-in;
  margin: 20px;
}
.quote:hover {
  background: #ffe1e3;
}
</style>