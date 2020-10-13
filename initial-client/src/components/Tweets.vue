<template>
	<section>
		<h2>Tweets</h2>
		<div class="tweet">
			<p class="tweet-info">
				<span></span>
			</p>
			<p>
			</p>
		</div>
	</section>
</template>

<script>
export default {};
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
