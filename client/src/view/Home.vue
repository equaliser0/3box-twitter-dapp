<template>
	<section class="tweet-container flex">
		<div class="header-container flex">
			<h1>"Twitter"</h1>
			<img src="@/assets/bird.png" />
		</div>

		<button class="connect-btn" @click="connect()" v-if="!connecting && !thread">
			Connect to App
		</button>

		<template v-else>
			<template v-if="connecting">
				<LoadingSpinner />
			</template>

			<template v-else>
				<h1>Hello, {{ userId }} 👋</h1>
				<SendTweet :thread="thread" :userId="userId" />
				<Suspense>
					<Tweets :thread="thread" />
				</Suspense>
			</template>
		</template>
	</section>
</template>

<script>
import Box from "3box";
import { onBeforeUnmount, ref } from "vue";

import Components from "@/components/index";

export default {
	components: {
		...Components
	},

	async setup() {
		const connecting = ref(false);
		const thread = ref(null);
		const userId = Math.random()
			.toString(36)
			.substring(7); // creates a random user id

		onBeforeUnmount(async () => {
			await thread.value.close();
		});

		async function connect() {
			try {
				connecting.value = true;

				const ethAccount = await window.ethereum.request({
					method: "eth_requestAccounts"
				});

				const box = await Box.openBox(ethAccount[0], window.ethereum);
				const space = await box.openSpace("twitter");
				await space.syncDone;

				thread.value = await space.joinThread("tweets", { ghost: true });
			} catch (error) {
				console.log(error);
			} finally {
				connecting.value = false;
			}
		}

		return {
			connecting,
			userId,
			thread,
			connect
		};
	}
};
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
