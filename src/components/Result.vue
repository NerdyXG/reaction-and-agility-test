<template>
    <p class="result">Reaction Time: {{ score }}ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: [
        "score"
    ],

    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if(this.score < 200) {
            this.rank = "Cat Reflex...you probably aren't human!"
        } else if(this.score < 250) {
            this.rank = "Ninja Fingers"
        } else if(this.score < 400) {
            this.rank = "Rapid Fingers"
        } else {
            this.rank = "Snail Pace..."
        }
    }
}
</script>

<style>
    .rank {
        font-weight: bold;
        color: #0000ff;
        font-size: 30px;
    }
</style>