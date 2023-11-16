<script>
	import '$lib/styles/global.css'
	import { data } from '$lib/scripts/data.js'

	import { onNavigate } from '$app/navigation'

	onNavigate((navigation) => {
		if (!document.startViewTransition) return

		return new Promise((resolve) => {
			document.startViewTransition(async () => {
				resolve()
				await navigation.complete
			})
		})
	})

	const currentYear = new Date().getFullYear()

	export const metaData = {
		title: data.title,
		description: `${data.role} based in ${data.location} with ${data.yearsOfExperience} years of experience - Portfolio of ${data.name}`,
		author: data.name,
		keywords: `${data.role}, ${data.location}, Portfolio, ${data.name}`
	}
</script>

<svelte:head>
	<title>{metaData.title}</title>
	<meta name="description" content={metaData.description} />
	<meta name="keywords" content={metaData.keywords} />
	<meta name="author" content={metaData.author} />
	<meta property="og:type" content="website" />
	<meta name="og:title" content={metaData.title} />
	<meta name="og:description" content={metaData.description} />
	<meta property="og:image" content="/img/og-image.jpg" />
	<meta name="theme-color" content="#000000" />
</svelte:head>

<div class="page">
	<main>
		<slot />
	</main>
	<footer class="container">
		<p>&copy; {currentYear} {data.name}</p>
	</footer>
</div>

<style>
	.page {
		display: grid;
		grid-template-columns: minmax(0, 1fr);
		grid-template-rows: 1fr auto;
		gap: var(--size-3);
		min-height: 100vh;
	}

	footer {
		display: flex;
		margin-block-end: var(--size-3);
	}

	footer p {
		margin: 0;
	}
</style>
