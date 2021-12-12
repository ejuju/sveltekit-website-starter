<script>
	import ArrowDown from '$lib/icons/ArrowDown.svelte';

	function scrollDown() {
		window.scrollTo({
			top: window.innerHeight,
			behavior: 'smooth'
		});
	}
</script>

<section class="HomeIntro">
	<h1>SvelteKit Starter Template</h1>
	<p>SSG, TypeScript, SCSS, global styles, basic components, and more</p>
	<nav>
		<button class="btn" on:click={scrollDown}><ArrowDown />Scroll down</button>
	</nav>

	<div class="HomeIntroBackground">
		<svg
			viewBox="0 0 900 900"
			xmlns="http://www.w3.org/2000/svg"
			xmlns:xlink="http://www.w3.org/1999/xlink"
			version="1.1"
		>
			<defs>
				<filter id="blur1" x="-10%" y="-10%" width="120%" height="120%">
					<feFlood flood-opacity="0" result="BackgroundImageFix" />
					<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape" />
					<feGaussianBlur stdDeviation="189" result="effect1_foregroundBlur" />
				</filter>
			</defs>
			<g filter="url(#blur1)">
				<circle cx="900" cy="0" fill="var(--c-2)" r="420" />
				<circle cx="0" cy="900" fill="var(--c-2)" r="420" />
				<circle cx="900" cy="900" fill="var(--c-1)" r="420" />
				<circle cx="791" cy="387" fill="var(--c-2)" r="420" />
				<circle cx="551" cy="866" fill="var(--c-1)" r="420" />
			</g>
		</svg>
	</div>
</section>

<style lang="scss">
	.HomeIntro {
		position: relative;
		min-height: calc(100vh - 3rem);
		padding: 1rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;

		h1 {
		}

		p {
			margin-top: 0.5rem;
			max-width: 40ch;
		}

		nav {
			margin-top: 1rem;
		}

		.HomeIntroBackground {
			z-index: -1;
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;

			background: var(--c-1);
			svg {
				height: 100%;
				width: 100%;
			}
		}
	}
</style>
