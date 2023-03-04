<script lang="ts">
	import H1 from "$lib/components/H1.svelte"

	let text: string = "woRld of waR  Craft   "
	$: text = text.replace(/[\\/:*?"<>\|]/g, " ")

	let extension = "js"
	$: extension = extension.replace(/\s/g, "")

	let result: Record<string, string> = {}
	$: result = {
		camelCase: text
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => (index === 0 ? word.toLowerCase() : word.toUpperCase()))
			.replace(/\s+/g, ""),
		"kebab-case": text.trim().toLowerCase().replace(/\s+/g, "-"),
		"lower case": text.trim().toLowerCase(),
		PascalCase: text
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, word => word.toUpperCase())
			.replace(/\s+/g, ""),
		snake_case: text.trim().toLowerCase().replace(/\s+/g, "_").toLowerCase(),
		"Title Case": text
			.trim()
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, word => word.toUpperCase())
			.replace(/\s+/g, " "),
		"UPPER CASE": text.trim().toUpperCase()
	}
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<H1 text="Home" />

<div class="grid grid-cols-6 gap-3">
	<textarea bind:value={text} class="col-span-2 col-start-3" />
	<input type="text" bind:value={extension} class="col-span-2 col-start-3 text-center" />
</div>

<table class="mx-auto table">
	<thead>
		<tr>
			<th />
			<th class="text-center">Result</th>
		</tr>
	</thead>
	<tbody>
		{#each Object.keys(result) as item}
			<tr class="hover">
				<td>{item}</td>
				<td>{result[item] + (text.trim().length && extension.length ? `.${extension}` : "")}</td>
			</tr>
		{/each}
	</tbody>
</table>

<div class="prose lg:prose-xl">
	{@html text}
</div>
