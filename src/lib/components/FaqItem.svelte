<script lang="ts">
	import Close from '$lib/icons/Close.svelte';

	import { slide } from 'svelte/transition';

	export let question: string;
	let expanded: boolean = false;
</script>

<section class="FaqItem" class:expanded>
	<button on:click={() => (expanded = !expanded)}>
		<Close />
		<h3>{question}</h3>
	</button>

	{#if expanded}
		<div transition:slide|local>
			<slot />
		</div>
	{/if}
</section>

<style lang="scss">
	.FaqItem {
		display: flex;
		flex-direction: column;

		button {
			width: 100%;
			display: flex;
			align-items: center;
			padding: 0.5rem 1rem;
			border: solid var(--bw) currentColor;

			h3 {
				font-size: 1rem;
			}

			:global(svg) {
				transition: transform 0.2s ease-in-out;
				transform: rotate(-45deg);
				margin-right: 0.75rem;
				font-size: 0.75rem;
			}

			&:hover {
				text-decoration: underline;
			}
		}

		div {
			border: solid var(--bw) currentColor;
			border-top: none;
			padding: 1rem;
		}

		&.expanded {
			button {
				background: var(--c-bg-1);
				:global(svg) {
					transform: rotate(0deg);
				}
			}
		}
	}
</style>
