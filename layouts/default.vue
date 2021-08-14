<template>
	<main class="page">
		<bael-header />
		<div class="page__body">
			<nuxt />
		</div>
		<!-- <lazy-slide-out />
    <bael-footer /> -->
	</main>
</template>
<script>
export default {
	data() {
		return {
			email: { email: "" },
		};
	},
	async middleware({ store, $content }) {
		await store.dispatch("fetchInfo", $content);
	},
};
</script>

<style lang="scss">
@import "~/assets/scss/helpers/variables.scss";
@import "~/assets/scss/helpers/mixin.scss";

.page {
	&__body {
		margin-left: 100px;
	}
}
</style>
