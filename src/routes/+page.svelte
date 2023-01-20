<script>
	let text = 'woRld of waRCraft   ';
	$: camelCase = text
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) =>
			index === 0 ? word.toLowerCase() : word.toUpperCase()
		)
		.replace(/\s+/g, '');
	$: kebabCase = text.trim().toLowerCase().replace(/\s/g, '-');
	$: lowerCase = text.trim().toLowerCase();
	$: pascalCase = text
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
		.replace(/\s+/g, '');
	$: snakeCase = text.trim().toLowerCase().replace(/\s/g, '_').toLowerCase();
	$: titleCase = text
		.trim()
		.toLowerCase()
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => word.toUpperCase())
		.replace(/\s+/g, ' ');
	$: upperCase = text.trim().toUpperCase();
	let extension = 'a';
</script>

<div class="text-center">
	<input type="text" bind:value={text} class="text-center" />
	<input type="text" bind:value={extension} class="text-center" />
</div>
<p>camelCase: {camelCase + (extension ? '.' + extension : '')}</p>
<p>kebab-case: {kebabCase + (extension ? '.' + extension : '')}</p>
<p>lower case: {lowerCase + (extension ? '.' + extension : '')}</p>
<p>PascalCase: {pascalCase + (extension ? '.' + extension : '')}</p>
<p>snake_case: {snakeCase + (extension ? '.' + extension : '')}</p>
<p>Title Case: {titleCase + (extension ? '.' + extension : '')}</p>
<p>UPPER CASE: {upperCase + (extension ? '.' + extension : '')}</p>
