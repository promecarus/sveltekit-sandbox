<script>
	let nav = [
		{
			name: "Case",
			href: "/"
		},
		{
			name: "Test",
			href: "/test"
		},
		{
			name: "Api",
			href: "/api"
		}
	]
</script>

<nav>
	{#each nav as { name, href }}
		<a {href}>{name}</a>
	{/each}
</nav>

<slot />
