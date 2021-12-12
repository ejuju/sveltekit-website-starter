<script>
	import { browser } from '$app/env';

	import { page } from '$app/stores';
	import config from '$lib/config/config';

	let expanded = false;

	$: {
		if (expanded === true) {
			window.document.body.style.overflowY = 'hidden';
		} else {
			if (browser) {
				window.document.body.style.overflowY = 'scroll';
			}
		}
	}

	page.subscribe(() => {
		closeMenu();
	});

	function toggleMenu() {
		expanded = !expanded;
	}

	function closeMenu() {
		expanded = false;
	}
</script>

<header class:expanded>
	<a href="/" class="Brand">{config.brandName}</a>

	<button on:click={toggleMenu} aria-label="Ouvrir le menu">
		<div />
	</button>

	<nav>
		<a href="/" class:active={$page.path === '/'}>Home</a>

		<a href="/404" class:active={$page.path === '/404'}>404 page</a>
		<a href="/mentions-legales" class:active={$page.path === '/mentions-legales'}>
			Legal notice (FR)
		</a>
	</nav>
</header>

<style lang="scss">
	header {
		position: relative;
		width: 100%;
		height: auto;
		z-index: 10;

		display: flex;
		align-items: center;
		justify-content: space-between;

		.Brand {
			font-weight: var(--fw-bold);
			padding: 1rem;
			padding-left: var(--s-s);
			text-decoration: none;

			display: flex;
			align-items: center;
		}

		button {
			position: relative;
			padding: 1.25rem 1.5rem;
			padding-right: var(--p-sides);

			&::before,
			&::after,
			& > div {
				content: '';
				position: absolute;
				right: 1rem;
				width: 1rem;
				height: 2px;
				background: currentColor;
				transition: transform 0.15s ease-in-out, top 0.15s ease-in-out;
			}

			&::before {
				top: 35%;
				transform: translateY(-50%);
			}
			& > div {
				top: 50%;
				transform: translateY(-50%);
				transition: opacity 0.1s ease-in-out;
			}

			&::after {
				top: 65%;
				transform: translateY(-50%);
			}
		}

		nav {
			position: absolute;
			top: 100%;
			left: -100%;
			width: 100%;
			height: calc(100vh - 100%);

			display: flex;
			flex-direction: column;

			overflow-y: scroll;
			background: var(--c-bg);
			transition: left 0.2s ease-out;

			a {
				border-bottom: solid 1px var(--c-bg-2);
				max-width: 100%;
				padding: 1rem var(--s-s);
				text-decoration: none;
				font-weight: var(--fw-bold);

				&:first-of-type {
					border-top: solid 1px var(--c-bg-2);
				}

				&:hover {
					text-decoration: underline;
				}

				&.active {
					color: var(--c-1);
				}
			}
		}

		&.expanded {
			button {
				& > div {
					opacity: 0;
				}
				&::before {
					top: 50%;
					transform: translateY(-50%) rotate(-45deg);
				}
				&::after {
					top: 50%;
					transform: translateY(-50%) rotate(45deg);
				}
			}

			nav {
				left: 0;
			}
		}

		@media (min-width: 800px) {
			button {
				display: none;
			}

			nav {
				top: auto;
				width: auto;
				height: auto;
				overflow-y: auto;
				display: flex;
				background: none;

				position: static;
				flex-direction: row;
				a {
					max-width: 100%;
					padding: 0.5rem 1rem;
					border: none !important;

					&:last-of-type {
						padding-right: var(--s-s);
					}
				}
			}
		}
	}
</style>
