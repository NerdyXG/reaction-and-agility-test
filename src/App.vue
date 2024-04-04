<template>
	<h1 class="title">Lightening Reflex Challenge</h1>
	<button class="btn" @click="play" :disabled="isPlaying">
		<span v-if="!isPlaying">Play</span>
		<span v-if="isPlaying">Be at alert...the block can appear at any time!</span>
	</button>

	<Block :blockContent="blockContent" v-if="isPlaying" :delay="delay" @end="endGame"/>
	<Result :score="score" v-if="showResult" />
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
export default {
	components: {
		Block,
		Result
	},

	data() {
		return {
			blockContent: "Click Here!",
			isPlaying: false,
			delay: 2000 + Math.round(Math.random()*5000),
			score: null,
			showResult: false
		}
	},

	methods: {
		play() {
			this.isPlaying = true
		},

		endGame(reactionTime) {
			this.score = reactionTime
			this.showResult = true
		}
	}
}
</script>

<style>
	.title {
		color: #0000ff;
		font-weight: 400;
		font-size: 30px;
	}

	.btn {
		border: 1px solid #000;
		background: transparent;
		padding: 5px 20px;
		border-radius: 7px;
		cursor: pointer;
		margin-top: 5px;
		transition: all ease 300ms;
	}

	.btn:hover {
		background: #0000ff;
		border: none;
		color: #fff;
	}

	.btn[disabled] {
		background: #0000ff;
		border: none;
		opacity: .5;
		color: #fff;
		cursor: not-allowed;
	}
</style>