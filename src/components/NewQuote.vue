<template>
    <div class="row">
        <div class="col-12 col-md-10 col-lg-8 mx-auto">
            <label for="newQuoteText" class="h1 display-3 text-center">Add new quote</label>
            <textarea name="newQuoteText" id="newQuoteText" rows="10" class="w-100 form-control mb-3" v-model="text"></textarea>
            <button role="button" class="btn btn-block btn-primary" :disabled="!mayAddQuote()" @click="createQuote">Add!</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "NewQuote",
        props: {
            maxQuotes: Number,
            quotesCount: Number
        },
        data() {
            return {
                text: ''
            }
        },
        methods: {
            createQuote() {
                if (this.text !== '' && this.mayAddQuote()) {
                    this.$emit('newQuoteCreated', this.text);
                    this.text = ''
                }
            },
            mayAddQuote() {
                return this.maxQuotes > this.quotesCount
            }
        }
    }
</script>

<style scoped>
    .btn:disabled{
        cursor: not-allowed;
    }

    h1{
        font-size: 4vh;
    }
</style>