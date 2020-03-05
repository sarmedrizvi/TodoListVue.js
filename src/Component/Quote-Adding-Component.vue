<template>
  <div class="quote-adding">
    <h5>Quote</h5>
    <textarea name="quoteSection" id cols="70" rows="3" v-model="quoteText"></textarea>
    <button @click="increaseQuote">Add-Quote</button>
  </div>
</template>


<script>
import { eventBus } from "../main.js";
export default {
  props: {
    totalQuotes: Number
  },
  data() {
    return {
      quoteText: "",
      quoteArray: [],
      total: this.totalQuotes,
    };
  },
  // computed: {
  //   getSetTotalQuotes: {
  //     get() {
  //       return this.totalQuotes;
  //     },
  //     set(value) {
  //       eventBus.$emit("totalQuotes", this.total);
  //     }
  //   }
  // },
  methods: {
    increaseQuote() {
      if (this.quoteText === "") {
        return alert("Not the way");
      }
      if (this.total === 10) {
        alert("Not more than 10");
        return;
      }

      this.quoteArray = [...this.quoteArray, this.quoteText];
      eventBus.$emit("quoteArrayEvent", this.quoteArray);
      this.quoteText = "";
      this.total++;
      eventBus.$emit("totalQuotes", this.total);
    }
  },
  created() {
    eventBus.$on("totalQuotes", data => {
      this.total = data;
    });
  }
};
</script>


<style scoped>
.quote-adding {
  display: grid;
  justify-content: center;
  grid-gap: 10px;
}
h5 {
  font-weight: bolder;
  justify-self: flex-start;
  font-weight: bolder;
}
button {
  background: #3278be;
  width: 100px;
  justify-self: center;
  color: white;
  padding: 6px;
  border-radius: 5px;
  border: 0.4px solid black;
  transition: background 0.3s ease-in-out;
}
button:hover {
  background: rgb(27, 68, 109);
}
textarea {
  border-radius: 2px;
  padding: 10px;
}
</style>