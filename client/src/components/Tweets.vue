<template>
	<section v-if="posts.length > 0">
		<h2>Tweets</h2>
		<div class="tweet" v-for="post in posts" :key="post.message.by">
			<p class="tweet-info">
				<span>{{ post.message.by }}</span> |
				{{ posted(post.message.timestamp) }} Minutes Ago
			</p>
			<p>
				{{ post.message.content }}
			</p>
		</div>
	</section>
</template>

<script>
import { ref } from "vue";

export default {
	props: {
		thread: {
			type: Object,
			required: true
		}
	},

	async setup(props) {
		const posts = ref([]);

		posts.value = await props.thread.getPosts();

		props.thread.onUpdate(async () => {
			posts.value = await props.thread.getPosts();
		});

		const posted = (timestamp) => {
			const start = new Date(timestamp).getMinutes();
			const end = new Date().getMinutes();

			const diff = end - start;
			return diff;
		};

		return {
			posts,
			posted
		};
	}
};
</script>

<style scoped>
.tweet {
	border: 1px solid gray;
	border-radius: 4px;
	width: 520px;
	margin-bottom: 10px;
}

.tweet p {
	padding: 10px;
	margin: 0;
}

.tweet-info {
	font-size: 0.75em;
}

.tweet-info span {
	color: var(--accent-color);
}
</style>
