<template>
	<div class="add-tweet-container flex"></div>
</template>

<script>
export default {};
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
