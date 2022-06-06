<script>
	import 'fluent-svelte/theme.css';
</script>

<div class="titlebar" />
<div class="spacer" />
<slot />

<style>
	:global(body) {
		background-color: var(--fds-solid-background-base);
		color: var(--fds-text-primary);
	}

	.titlebar {
		display: block;
		position: fixed;
		height: 48px;
		top: 0;
		left: 0;
		width: calc(100% - 2px);
		z-index: 999;
		background: #333333;
	}
	.spacer {
		width: 100%;
		height: 48px;
	}
</style>
