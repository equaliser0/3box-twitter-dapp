<template>
	<div class="add-tweet-container flex">
		<textarea
			v-model.trim="content"
			placeholder="Write Something"
			maxlength="250"
		></textarea>
		<button @click="sendTweet()">Send Tweet</button>
	</div>
</template>

<script>
import { ref } from "vue";

export default {
	props: {
		userId: {
			type: String,
			required: true
		},

		thread: {
			type: Object,
			required: true
		}
	},

	setup(props) {
		const content = ref("");

		async function sendTweet() {
			props.thread.post({
				content: content.value,
				by: props.userId,
				timestamp: new Date().getTime()
			});
		}

		return {
			sendTweet,
			content
		};
	}
};
</script>

<style scoped>
.add-tweet-container {
	flex-direction: column;
	align-items: center;
	width: 500px;
	height: 250px;
}

.add-tweet-container textarea {
	width: 100%;
	height: 100%;
	font-size: 1.333em;
	border-radius: 8px;
	resize: none;
	border-style: none;
	border-color: transparent;
	overflow: auto;
	padding: 8px;
}

.add-tweet-container button {
	background: var(--accent-color);
	color: var(--main-color);
	margin-top: 20px;
}
</style>
