<template>
  <div class="container">
    <app-Header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-Header>
    <app-New-Quote @quoteAdded="newQuote"></app-New-Quote>
    <app-Quote-Grid :quotes="quotes" @quoteDeleted="quoteDeleted"></app-Quote-Grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";

export default {
  data: function () {
    return {
      quotes: ["Just a Quote to see something"],
      maxQuotes: 10,
    };
  },
  methods: {
    newQuote(quoteToAdd) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please delete Quote first");
      }
      this.quotes.push(quoteToAdd);
    },
    quoteDeleted(index) {
      this.quotes.splice(index, 1);
    },
  },
  components: {
    "app-Quote-Grid": QuoteGrid,
    "app-New-Quote": NewQuote,
    "app-Header": Header,
  },
};
</script>

<style>
</style>
