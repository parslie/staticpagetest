<script>
	import Fa from 'svelte-fa';
	import { faHome, faVial, faUtensils } from '@fortawesome/free-solid-svg-icons';

	import { page } from '$app/stores';
	let currPath = $page.url.pathname;
</script>

<div class="layout">
	<header>
		<aside>
			<div class="corner left"><div class="filling"></div></div>
			<div class="corner right"><div class="filling"></div></div>
			<span class="title">Viktor Holta</span>

			<nav>
				<a href="/" class={currPath == '/' ? 'current' : undefined}>
					<Fa icon={faHome} />
					Home
				</a>
				<hr />
				<a href="/test" class={currPath == '/test' ? 'current' : undefined}>
					<Fa icon={faVial} />
					Test
				</a>
				<hr />
			</nav>

			<slot name="aside" />
		</aside>
	</header>

	<main>
		<slot />
	</main>
</div>

<style lang="scss">
	$gradient: linear-gradient(135deg, $primary, $secondary);

	.layout {
		position: absolute;
		top: 0;
		left: 0;
		width: 100dvw;
		min-height: 100dvh;
		background-color: $background;
		color: $text;
	}

	header {
		position: fixed;
		top: 0;
		left: 0;
		width: 100dvw;
		height: $sub-header-height;

		background: $gradient;
		background-position: 0 0;
		background-size: 100dvw 100dvh;
		line-height: 1;
	}

	aside {
		position: relative;
		top: $sub-header-height;
		left: $sub-padding;
		width: $sub-aside-width;
		min-height: $sub-radius + $sub-aside-padding;
		padding: 0 $sub-aside-padding $sub-aside-padding;
		border-radius: 0 0 $sub-radius $sub-radius;

		background: $gradient;
		background-position: (-$sub-padding) (-$sub-header-height);
		background-size: 100dvw 100dvh;
		color: $background;

		.corner {
			position: absolute;
			top: 0;
			width: $sub-padding;
			height: $sub-padding;

			background: $gradient;
			background-size: 100dvw 100dvh;

			.filling {
				width: 100%;
				height: 100%;
				background-color: $background;
			}

			&.left {
				left: (-$sub-padding);
				.filling {
					border-top-right-radius: $sub-radius;
				}
			}

			&.right {
				right: (-$sub-padding);
				background-position: (-$sub-padding - $sub-aside-width) (-$sub-header-height);
				.filling {
					border-top-left-radius: $sub-radius;
				}
			}
		}

		.title {
			display: block;
			text-align: center;
			font-size: 3.29em;
			font-weight: bold;
			text-wrap: nowrap;
		}

		*:last-child {
			margin-bottom: 0;
		}
	}

	nav {
		display: flex;
		flex-direction: column;
		margin: 0.5rem 0;
		border-radius: 0.3rem;
		background-color: rgba(0, 0, 0, 0.1);
		overflow: hidden;

		a {
			padding: 0.4rem 0.5rem;
			color: $background;
			text-decoration: none;
			font-weight: bold;

			&:hover,
			&.current {
				background-color: rgba(0, 0, 0, 0.15);
			}
		}

		hr {
			border: 0;
			border-bottom: 1px solid rgba(0, 0, 0, 0.15);
		}
	}

	main {
		position: relative; // Needed to make content interactable
		margin: ($sub-header-height + $sub-padding) $sub-padding $sub-padding
			(2 * $sub-padding + $sub-aside-width);
		line-height: 1;
	}
</style>
