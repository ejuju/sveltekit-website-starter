<script context="module">
	export function load({ error, status }) {
		return {
			props: {
				title: `${status} ${error.message}`
			}
		};
	}
</script>

<script>
	export let title;
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<main>
	<h1>Erreur - {title}</h1>

	<nav>
		<a href="/" class="btn">Retourner à la page d'accueil</a>
	</nav>
</main>

<style lang="scss">
	main {
		padding: var(--p-page);
		display: flex;
		flex-direction: column;

		h1 {
			color: var(--clr-txt-2);
			border: none;
		}

		nav {
			margin-top: 1rem;
			display: flex;
			flex-wrap: wrap;
			row-gap: 1rem;
			column-gap: 1rem;
		}
	}
</style>
