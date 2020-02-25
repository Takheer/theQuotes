<template>
    <transition-group tag="div" class="row" name="slide" appear>
        <app-quote v-for="(quote, index) in quotes" :key="quote" :quote="quote" @click.native="deleteQuote(index)">
        </app-quote>
    </transition-group>
</template>

<script>
    import Quote from "./Quote";
    export default {
        name: "QuoteGrid",
        components: {appQuote: Quote},
        props: {
            quotes: Array
        },
        methods: {
            deleteQuote(index) {
                this.$emit('quoteDeleted', index)
            }
        }
    }
</script>

<style lang="scss" scoped>
    p{
        font-size: 5vh;
    }
    .slide {
        &-enter {
            &-active{
                animation: slide-in 1s ease-out forwards;
            }
        }

        &-leave {
            &-active {
                animation: slide-out 1s ease-in forwards;
                position: absolute;
            }
        }

        &-move {
            transition: transform 2s;
        }
    }

    @keyframes slide-in {
        from {
            transform: translateX(20px);
            opacity: 0;
        }
        to {
            transform: translateX(0);
            opacity: 1;
        }
    }

    @keyframes slide-out {
        from {
            transform: translateX(0);
            opacity: 1;
        }
        to {
            transform: translateX(20px);
            opacity: 0;
        }
    }
</style>