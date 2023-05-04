<script lang="ts">
	export let title: string;
</script>

<svelte:head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width" />
	<link rel="icon" type="image/svg+xml" href="/mylogo.ico" />
	<meta name="description" content="=まなさすが作ったツール集" />
	<meta property="og:site_name" content="manasandbox" />
	<meta property="og:title" content={title} />
	<meta property="og:url" content="https://tools.manasas.dev" />
	<meta property="og:description" content="まなさすが作ったツール集" />
	<meta property="og:image" content="https://tools.manasas.dev/aza166.png" />
	<title>{title}</title>
</svelte:head>

<body>
	<header>
		<h1><a href="/">Mana's tools</a></h1>
	</header>
	<main>
		<slot />
	</main>
	<footer><a href="https://manasas.dev/" rel="me">© 2022 Manami SASAKI</a></footer>
</body>

<style lang="scss">
	body {
		margin: 0;
	}
	a {
		color: #fff;
		text-decoration: none;
	}
	header {
		background: #44617b;
		color: #fff;
		vertical-align: baseline;
		padding: 4px 8px;
		line-height: 1.5;
		& > h1 {
			margin: 0;
			font-size: 1.25rem;
			font-weight: 300;
		}
	}
	footer {
		background: #44617b;
		color: #fff;
		text-align: center;
		padding: 4px 8px;
		line-height: 1.5;
	}
	main {
		max-width: 800px;
		margin: 0 auto;
		min-height: calc(100vh - 1.25rem * 1.5 - 8px - 1rem * 1.5 - 8px);
	}
	@media only screen and (max-width: 500px) {
		header > h1 {
			font-size: 18px;
		}
	}
</style>
