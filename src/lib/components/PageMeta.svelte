<script>
	import config from '$lib/config/config';

	export let title;
	export let description;

	// TODO: support schema markup, OG things for social media sharing
</script>

<svelte:head>
	<title>{title} - {config.brandName}</title>
	<meta name="description" content={description} />
</svelte:head>
