<script>
	let text = 'woRld of waRCraft';
	$: camelCase = text
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) =>
			index === 0 ? word.toLowerCase() : word.toUpperCase()
		)
		.replace(/\s+/g, '');
	$: kebabCase = text.toLowerCase().replace(/\s/g, '-');
	$: lowerCase = text.toLowerCase();
	$: pascalCase = text
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
		.replace(/\s+/g, '');
	$: snakeCase = text.toLowerCase().replace(/\s/g, '_').toLowerCase();
	$: titleCase = text
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
		.replace(/\s+/g, ' ');
	$: upperCase = text.toUpperCase();
</script>

<div class="text-center">
	<input type="text" bind:value={text} class="text-center" />
</div>
<p>camelCase: {camelCase}</p>
<p>kebab-case: {kebabCase}</p>
<p>lower case: {lowerCase}</p>
<p>PascalCase: {pascalCase}</p>
<p>snake_case: {snakeCase}</p>
<p>Title Case: {titleCase}</p>
<p>UPPER CASE: {upperCase}</p>
