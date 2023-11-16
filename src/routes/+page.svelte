<script>
	import { data } from '$lib/scripts/data.js'
	import Email from '$lib/icons/email.svelte'

	const github = 'https://github.com/zukinii'

	// assemble email to avoid bots reading it
	const openEmail = () => {
		const emailUserParts = ['dominic', 'ma', 'pranz']
		const emailAlias = 'portfolio'
		const emailDomainParts = ['gmail', 'com']
		const email = `${emailUserParts.join('.')}+${emailAlias}@${emailDomainParts.join('.')}`
		const mailtoLink = `mailto:${email}`
		window.location.href = mailtoLink
	}
</script>

<header class="container">
	<h1>{data.name}</h1>
	<p>
		{data.role} based in {data.location}
		<a href="/experience">with {data.yearsOfExperience} years of experience</a>
	</p>
	<button on:click={openEmail}><Email /> Contact me</button>
</header>

<style>
	header {
		min-height: 100%;
		display: grid;
		align-content: center;
		justify-items: center;
		text-align: center;
	}

	p {
		max-inline-size: var(--size-content-2);
	}

	button {
		display: flex;
		align-items: center;
		gap: var(--size-3);
		background-color: var(--brand);
		margin-block-start: var(--size-7);
		padding: var(--size-2);
		border-radius: var(--radius-2);
		box-shadow: var(--shadow-1);

		&:hover,
		&:focus-visible {
			background-color: var(--brand-dark);
		}
	}
</style>
