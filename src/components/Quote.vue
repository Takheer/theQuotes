<template>
        <div class="col-xs-12 col-md-6 col-lg-3 p-3">
            <div class="frame h-100 p-2">
                <p class="lead mb-auto">{{ quote }}</p>
            </div>
        </div>
</template>

<script>
    export default {
        name: "Quote",
        props: {
            quote: String
        },
    }
</script>

<style lang="scss" scoped>
    .frame {
        border: 1px solid #ccc;
        border-radius: 7px;
        box-shadow: 1px 2px 3px #aaa;
        transition: all .2s ease-in-out;
        p {
            font-family: 'Arizonia', Rockwell, sans-serif;
            font-size: 26px;
        }
        &:hover {
            background-color: lemonchiffon;
            box-shadow: 2px 4px 6px #999;
            cursor: pointer;
        }
    }
</style>