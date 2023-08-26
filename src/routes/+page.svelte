<script>
	import { camelCase, kebabCase, lowerCase, upperFirst, snakeCase, startCase, upperCase, trim } from "lodash"

	let text = "Among Us"

	let extension = "js"
	$: extension = trim(extension)

	/**
	 * @type {Object<string, string>}
	 * */
	let result = {}
	$: result = {
		camelCase: camelCase(text),
		"kebab-case": kebabCase(text),
		"lower case": lowerCase(text),
		PascalCase: upperFirst(camelCase(text)),
		snake_case: snakeCase(text),
		"Title Case": startCase(text),
		"UPPER CASE": upperCase(text)
	}
</script>

<svelte:head>
	<title>Case</title>
</svelte:head>

<h1>Case</h1>

<textarea bind:value={text} />
<input type="text" bind:value={extension} />

<table>
	<tbody>
		{#each Object.keys(result) as item}
			<tr>
				<td>{item}</td>
				<td>{result[item] + (text.trim().length && extension.length ? `.${extension}` : "")}</td>
				<td><button on:click={() => navigator.clipboard.writeText(result[item] + (text.trim().length && extension.length ? `.${extension}` : ""))}>Copy</button></td>
			</tr>
		{/each}
	</tbody>
</table>
