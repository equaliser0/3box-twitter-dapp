<template>
	<main>
		<Suspense>
			<Home />
		</Suspense>
	</main>
</template>

<script>
import Home from "./view/Home";

export default {
	components: {
		Home
	}
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap");

:root {
	--main-bg-color: #15202b;
	--secondary-bg-color: #657786;

	--main-color: #ffffff;
	--accent-color: #1d8dee;
}

.flex {
	display: flex;
}

html {
	font-family: Poppins;
	background: var(--main-bg-color);
	color: var(--main-color);
}

button {
	border: none;
	outline: none;
	font-size: 1.333em;
	border-radius: 8px;
	padding: 10px;
	font-weight: bold;
}

button:hover {
	cursor: pointer;
}
</style>
