<template>
  <div id="app" class="container">
    <app-header :max-quotes="maxQuotes"
                :quotes-count="quotesArray.length"></app-header>
    <app-new-quote :max-quotes="maxQuotes"
                   :quotes-count="quotesArray.length"
                   @newQuoteCreated="addQuote"></app-new-quote>
    <quote-grid :quotes="quotesArray" @quoteDeleted="deleteQuote"></quote-grid>
    <div class="alert alert-primary w-100 mt-3">Click the quote to delete it</div>
    <br>
    <app-text-button :text="'Press!'" :horizontal-margin="6" :vertical-margin="0"></app-text-button>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
import NewQuote from "./components/NewQuote";
import Header from "./components/Header";
import TextButton from "./components/TextButton";

export default {
  name: 'App',
  components: {
    QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header,
    appTextButton: TextButton
  },
  data(){
    return {
      quotesArray: ['something to have', 'something to be', 'something to use'],
      maxQuotes: 10,
      width: 0
    }
  },
  methods: {
    addQuote(quote) {
      this.quotesArray.unshift(quote)

    },
    deleteQuote(index){
      this.quotesArray.splice( index, 1 )
    }
  }
}
</script>

<style lang="scss">
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}

</style>
