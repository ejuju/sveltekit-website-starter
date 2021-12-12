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
				<circle cx="900" cy="0" fill="#FF0066" r="420" />
				<circle cx="0" cy="900" fill="#FF0066" r="420" />
				<circle cx="900" cy="900" fill="#6600FF" r="420" />
				<circle cx="791" cy="387" fill="#FF0066" r="420" />
				<circle cx="551" cy="866" fill="#6600FF" r="420" />
			</g>
		</svg>
	</div>
</section>

<style lang="scss">
	.HomeIntro {
		position: relative;
		min-height: 100vh;
		padding: 1rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		h1 {
			text-align: center;
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

			background: #6600ff;
			svg {
				height: 100vh;
				width: 100%;
			}
		}
	}
</style>
