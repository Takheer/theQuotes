<template>
    <div>
        <h3 class="display-4">Quotes Added: </h3>
        <div class="progress">
            <div class="progress-bar" role="progressbar" :style="{ 'width': completeness() + '%'}" :aria-valuenow="completeness()" aria-valuemin="0" aria-valuemax="100">
                {{ quotesCount }} / {{ maxQuotes }}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Header",
        props: {
            maxQuotes: Number,
            quotesCount: Number
        },
        calculated: {
        },
        data() {
            return {
            }
        },
        methods: {
            completeness() {
                return this.quotesCount / this.maxQuotes * 100
            }
        }
    }
</script>

<style scoped>
    h3{
        font-size: 6vh;
    }
</style>