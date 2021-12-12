<script>
	import config from '$lib/config/config';
</script>

<footer>
	<p class="BrandSignature">
		{config.brandName}
		© {new Date().getFullYear()}
	</p>
</footer>

<style lang="scss">
	footer {
		padding: 1rem var(--s-s);
	}
</style>
