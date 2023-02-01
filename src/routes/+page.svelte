<script lang="ts">
	let text: string = "woRld of waR  Craft   "
	let extension = "js"
	$: extension = extension.replace(/\s/g, "")

	$: result = {
		camelCase: text
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => (index === 0 ? word.toLowerCase() : word.toUpperCase()))
			.replace(/\s+/g, ""),
		"kebab-case": text.trim().toLowerCase().replace(/\s+/g, "-"),
		"lower case": text.trim().toLowerCase(),
		PascalCase: text
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
			.replace(/\s+/g, ""),
		snake_case: text.trim().toLowerCase().replace(/\s+/g, "_").toLowerCase(),
		"Title Case": text
			.trim()
			.toLowerCase()
			.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
			.replace(/\s+/g, " "),
		"UPPER CASE": text.trim().toUpperCase()
	}
</script>

<article class="prose lg:prose-xl">
	<h1>halo</h1>
	{@html text}
</article>

<div class="text-center">
	<input type="text" bind:value={text} class="text-center" />
	<input type="text" bind:value={extension} class="text-center" />
</div>

<div class="mx-auto">
	<table class="m-5 table w-12">
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
</div>
