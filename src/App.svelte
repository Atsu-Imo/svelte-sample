<script>
    import { onMount } from 'svelte'

	let channels =[];
	onMount(async () => {
		const response = await fetch('http://localhost:1323/channels', {
			mode: "cors",
		});
		channels = await response.json();
	});
</script>

<main>
	{#each channels as c}
	    <div>{c.ChannelID}</div>
	    <div>{c.Title}</div>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>