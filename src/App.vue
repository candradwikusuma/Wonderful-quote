<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="NewQuote"></app-new-quote>
    <app-quote-grid
      :quotes="quotes"
      @quoteDeleted="quoteDeleted"
    ></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center mt-3">
        <div class="alert alert-info">info: Click on a Quote to Delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import NewQuote from "./component/NewQuote.vue";
import QuoteGrid from "./component/QuoteGrid.vue";
import Header from "./component/Header.vue";
export default {
  data() {
    return {
      quotes: ["Just a Quote to see something"],
      maxQuotes: 10
    };
  },
  methods: {
    NewQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("please delete the quotes first");
      }
      this.quotes.push(quote);
    },
    quoteDeleted(index) {
      this.quotes.splice(index, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  }
};
</script>

<style></style>
