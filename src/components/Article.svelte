<article><slot /></article>

<style lang="scss">
	article {
		display: grid;
		grid-template-columns: 1fr;
		grid-template-rows: 1fr;
		padding: $article-padding;
		border-radius: $article-radius;
		background: linear-gradient(135deg, $primary, $secondary);
	}
</style>
