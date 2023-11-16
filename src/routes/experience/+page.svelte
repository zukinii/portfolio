<script>
	import { data } from '$lib/scripts/data.js'
	import ChevronLeft from '$lib/icons/chevron-left.svelte'

	const workExperience = [
		{
			year: '2016 - 2019',
			company: 'Salzburg Digital / Salzburger Nachrichten',
			companyUrl: 'https://www.sn.at/',
			role: 'Fullstack Web Developer',
			technologies: ['PHP', 'MySQL', 'Wordpress'],
			description:
				'Relaunch of the Salzburger Nachrichten website and development + maintenance of Wordpress sites and internal tools',
			examples: [
				'https://www.salzburg24.at/',
				'https://www.karriereforum.eu/',
				'https://www.svh.at/'
			]
		},
		{
			year: '2020 - 2021',
			company: 'A365',
			companyUrl: 'https://www.a365.at/',
			role: 'Frontend Web Developer',
			technologies: ['CSS', 'React', 'Typo3'],
			description: 'Relaunch of the A365 website and frontend development of all client websites',
			examples: [
				'https://www.marcel-eberharter.com/',
				'https://www.hygcen.at/',
				'https://www.mcm.at/',
				'https://www.polistar.at/',
				'https://www.funktionsdecke.at/'
			]
		},
		{
			year: '2021 - now',
			company: 'LOOP',
			companyUrl: 'https://www.agentur-loop.com/',
			role: 'Frontend Web Developer',
			technologies: ['HTML', 'CSS', 'JavaScript'],
			description: 'Frontend development of client websites',
			examples: [
				'https://www.story.one/',
				'https://www.tjs.at/',
				'https://www.redbullring.com/',
				'https://www.ottakringerbrauerei.at/',
				'https://www.muellermobile.de/'
			]
		}
	]
</script>

<svelte:head>
	<title>{data.title} - Experience</title>
</svelte:head>

<section class="container">
	<a href="/" class="back-link"><ChevronLeft /> Back</a>

	<h1>Work Experience</h1>

	{#each workExperience as work}
		<article>
			<h2>{work.year}</h2>
			<h3><a href={work.companyUrl} target="_blank">{work.company}</a></h3>
			<p>{work.role}</p>
			<p>{work.description}</p>
			<ul>
				{#each work.technologies as technology}
					<li>{technology}</li>
				{/each}
			</ul>
			<ul>
				{#each work.examples as example}
					<li><a href={example} target="_blank">{example}</a></li>
				{/each}
			</ul>
		</article>
	{/each}

	<article>
		<h2>Other Stuff</h2>
		<ul>
			<li>
				<a href="https://zukinii.github.io/homepage/" target="_blank">My old personal website</a>
			</li>
		</ul>
	</article>
</section>

<style>
	section {
		display: grid;
		gap: var(--size-3);
		margin-block-start: var(--size-5);
	}

	.back-link {
		display: flex;
		align-items: center;
		gap: var(--size-2);
		margin-block-end: var(--size-7);
	}

	article {
		&:not(:last-of-type) {
			border-block-end: 1px solid currentColor;
		}
	}

	article ul li {
		&:not(:last-of-type) {
			margin-block-end: var(--size-1);
		}
	}
</style>
