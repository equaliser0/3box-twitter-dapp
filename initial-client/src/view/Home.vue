<template>
	<section class="tweet-container flex">
		<div class="header-container flex">
			<h1>"Twitter"</h1>
			<img src="@/assets/bird.png" />
		</div>
	</section>
</template>

<script>
export default {};
</script>

<style scoped>
.tweet-container {
	flex-direction: column;
	align-items: center;
}

.tweet-container button {
	align-self: flex-start;
	background-color: orangered;
	color: var(--main-color);
	margin: 20px 0 0 20px;
}

.header-container h1 {
	font-size: 3em;
	color: var(--accent-color);
}

.header-container img {
	padding-top: 18px;
	padding-left: 20px;
	max-width: 64px;
	max-height: 64px;
}

.connect-btn {
	margin: auto !important;
}
</style>
