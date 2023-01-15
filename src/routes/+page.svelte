<script>
	let name = 'world';
	const handleClick = () => (name = name === 'world' ? 'SvelteKit' : 'world');
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<h1 class="text-3xl font-bold underline">Hello {name}!</h1>
<input type="text" bind:value={name} />
<button on:click={handleClick}> Click me </button>
