<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        <p>{{ blockContent }}</p>
    </div>
</template>

<script>
export default {
    props: [
        "blockContent",
        "delay"
    ],

    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },

        stopTimer() {
            clearInterval(this.timer)
            this.showBlock = false
            this.$emit("end", this.reactionTime)
            console.log(this.reactionTime)
        }
    },

    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    }
}
</script>

<style>
    .block {
        width: 400px;
        height: 200px;
        margin: 20px auto;
        background: #0000ff;
        border-radius: 20px;
        color: #fff;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all ease-in 300ms;
    }

    .block:hover {
        opacity: .7;
        box-shadow: 6px 6px 16px #cccccc;
    }

    .block p {
        font-weight: bold;
    }
</style>