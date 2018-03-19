<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <app-info></app-info>
    </div>
</template>

<script>
    import Header from './Components/Header.vue';
    import NewQuote from './Components/NewQuote.vue';
    import QuoteGrid from './Components/QuoteGrid.vue';
    import Info from './Components/Info.vue';
    
    
    export default {
        data: function() {
            return {
                quotes: [
                    'Just a Quote'
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    return alert('Please delete some Quotes first');
                }
                this.quotes.push(quote)
            },
            deleteQuote(index) {
                this.quotes.splice(index,1);
            }
        },
        components: {
            appHeader: Header,
            appNewQuote: NewQuote,
            appQuoteGrid: QuoteGrid,
            appInfo: Info
        }
    }
</script>

<style>
</style>


