<script>
	import { navigating } from '$app/stores';

	import Footer from '$lib/components/Footer.svelte';
	import Header from '$lib/components/Header.svelte';

	import '../styles/manifest.scss';
</script>

{#if $navigating}
	<div class="NavigatingIndicator" class:navigating={$navigating} />
{/if}

<Header />
<slot />
<Footer />

<style lang="scss">
	.NavigatingIndicator {
		z-index: 1000;
		pointer-events: none;
		position: fixed;
		top: 0;
		left: 0;
		width: 0%;
		height: 1px;
		display: flex;
		background: var(--clr-1);

		&.navigating {
			animation: loading 2s infinite ease-in-out;
			animation-delay: 0.2s;
		}
		@keyframes loading {
			50% {
				left: 0;
				width: 100%;
			}

			100% {
				left: 100%;
				width: 0%;
			}
		}
	}
</style>
