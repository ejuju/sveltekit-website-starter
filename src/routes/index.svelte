<script>
	import HomeIntro from '$lib/components/HomeIntro.svelte';
	import Header from '$lib/components/Header.svelte';
	import PageMeta from '$lib/components/PageMeta.svelte';
	import FaqItem from '$lib/components/FaqItem.svelte';

	const components = [
		{
			title: 'Header [x]',
			description:
				'Used for SEO. Helps set page meta data easily (including title, meta description, json-ld, OG stuff)'
		},
		{
			title: 'Footer [ ]',
			description:
				'Used for SEO. Helps set page meta data easily (including title, meta description, json-ld, OG stuff)'
		},
		{
			title: 'PageMeta [ ]',
			description:
				'Used for SEO. Helps set page meta data easily (including title, meta description, json-ld, OG stuff)'
		},
		{
			title: 'HomeIntro [x]',
			description: 'Home page intro section. Outsourced for convenience'
		},
		{
			title: 'FaqItem [ ]',
			description: 'FAQs == good'
		}
	];
</script>

<PageMeta title="Home" description="I'm the page meta description" />

<main>
	<HomeIntro />

	<section class="Overview">
		<h2>Overview</h2>
		<p>Here's what included in the starter template</p>
		<ul>
			<li>[x] SSG</li>
			<li>[x] SCSS</li>
			<li>[x] TypeScript</li>
			<li>[x] <a href="/page-that-doesnt-exist">Error / 404 Page</a></li>
			<li>[x] Global styles</li>
			<li>[x] Icons</li>
			<li>[X] Basic components</li>
			<li>[ ] Easy config</li>
			<li>[ ] Sitemap.xml</li>
			<li>[ ] SEO friendly (robots.txt, sitemap, meta data, etc.)</li>
		</ul>
	</section>

	<section class="Components">
		<h2>Basic components</h2>
		<div class="Wrap">
			{#each components as c}
				<section class="Item">
					<h3>{c.title}</h3>
					<p>{c.description}</p>
					{#if c.component}
						<div class="WrapComponent">
							<svelte:component this={c.component} />
						</div>
					{/if}
				</section>
			{/each}
		</div>
	</section>

	<section class="FAQ">
		<h2>FAQ</h2>
		<FaqItem question="Are there upcoming features ?">
			<p>Yes...</p>
			<ul>
				<li>[ ] i18n</li>
				<li>[ ] Headless CMS integration (Strapi?)</li>
			</ul>
		</FaqItem>
	</section>
</main>

<style lang="scss">
	main {
		padding-bottom: var(--s-pagebottom);

		& > :global(.HomeIntro) {
			min-height: 100vh;
		}

		.Overview,
		.Components,
		.FAQ {
			margin-top: 4rem;
			padding: 0 var(--s-s);
		}

		.Overview,
		.FAQ {
			p {
				margin-top: 0.5rem;
			}

			ul {
				margin-top: 1rem;
				display: flex;
				flex-wrap: wrap;
				gap: 0.5rem;
				li {
					padding: 0.125rem 0.5rem;
					border: solid 1px var(--c-bg-2);
				}
			}
		}

		.Components {
			.Wrap {
				margin-top: 0.5rem;

				display: grid;
				grid-template-columns: 1fr;
				gap: 1rem;

				@media (min-width: 800px) {
					grid-template-columns: 1fr 1fr 1fr;
				}

				.Item {
					padding: 1rem;
					border: solid var(--bw) var(--c-bg-1);
					max-height: 50vh;

					h3 {
						font-family: var(--font-mono);
					}

					p {
						margin-top: 0.25rem;
					}

					.WrapComponent {
						height: 100%;
						margin-top: 1rem;
					}
				}
			}
		}

		.FAQ {
			:global(.FaqItem) {
				margin-top: 1rem;
			}
		}
	}
</style>
