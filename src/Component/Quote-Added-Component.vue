<template>
  <div class="quote-added">
    <h1>Quotes Added</h1>
    <div class="progress-bar-back">
      <div id="progress-bar" :style="{width: (total *10) + '%'}">
        <div :style="{paddingLeft: (total*45)+ 'px',display:'flex'}">
          <span>{{total}}</span> /
          <span>10</span>
        </div>
      </div>
    </div>
    <!-- <button @click="totalQuote++">Increase</button> -->
  </div>
</template>


<script>
import { eventBus } from "../main.js";
export default {
  data() {
    return {
      total: this.totalQuotes
    };
  },
  props: {
    totalQuotes: Number
  },
  created() {
    eventBus.$on("totalQuotes", data => {
      this.total = data;
    });
  }
};
</script>


<style scoped >
.quote-added {
  margin: 50px 0px;
}
h1 {
  font-weight: bolder;
}
#progress-bar {
  padding: 1px 2px;
  color: white;
  display: flex;
  background: #3278be;
  border-radius: 5px 0px 0px 5px;
  transition: all 0.5s linear;
}
.progress-bar-back {
  border-radius: 5px;
  background: rgb(241, 239, 239);
  box-shadow: 1px 1px 1px rgb(192, 191, 191);
}
</style>