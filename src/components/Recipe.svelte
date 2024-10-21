<script>
	import Article from './Article.svelte';

	export let image;
	export let name;
	export let source;
	export let sourceName;
	export let recipeUrl;
</script>

<Article>
	<div class="recipe">
		<header>
			<span class="name"><a href={`/recipes/${recipeUrl}`}>{name}</a></span>
			<span class="source">Source: <a href={source}>{sourceName}</a></span>
		</header>
		<img src={image} alt={name} />
	</div>
</Article>

<style lang="scss">
	.recipe {
		display: flex;
		flex-direction: column;
		border-radius: $article-inner-radius;

		header {
			flex-grow: 1;
			padding: 0.4rem;
			color: $background;
		}

		.name {
			display: block;
			font-size: 1.4rem;
			font-weight: bold;
		}

		img {
			display: block;
			border-radius: $article-inner-radius;
			width: 100%;
		}
	}
</style>
