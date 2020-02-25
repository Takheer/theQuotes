<template>
    <pre>
        {{ horizontalBorder }}
        {{ textLine }}
        {{ horizontalBorder }}
    </pre>
</template>

<script>
    export default {
        name: "TextButton",
        props: {
            text: String,
            horizontalMargin: {
                type: Number,
                default: 3
            },
            verticalMargin: {
                type: Number,
                default: 0
            },
            color: {
                text: {
                    type: String,
                    default: 'black'
                },
                hover: {
                    type: String,
                    default: 'red'
                }
            }
        },
        methods: {
            emptySpace(n) {
                let lines = [];
                if (n === 0) {
                    return
                }
                for (let i = 0; i < n; i++) {
                    lines.push('|' + ' '.repeat(this.text.length + this.horizontalMargin * 2)  + '|')
                }
                return lines.join('\n')

            }
        },
        computed: {
            horizontalBorder() {
                return '+' + '-'.repeat(this.text.length + this.horizontalMargin * 2) + '+'
            },
            textLine() {
                return '|' + ' '.repeat(this.horizontalMargin) + this.text + ' '.repeat(this.horizontalMargin) + '|'
            }
        }
    }
</script>

<style lang="scss" scoped>
    pre {
        display: inline;
        font-family: 'Roboto Mono', monospace;
        background-color: transparent;
        color: black;
        cursor: pointer;
        transition: color .2s ease-in;
        &:hover {
            color: red;
        }
    }
</style>