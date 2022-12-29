<script>
	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];
</script>
<h1>Each Block</h1>
<h3>The Famous Cats of YouTube</h3>

<!-- Each block without iteration count (aka "i") -->
<ul>
	{#each cats as { id, name }}
		<li>
			<a target="_blank" rel="noreferrer" href="https://www.youtube.com/watch?v={id}">
				{name}
			</a>
		</li>
	{/each}
</ul>

<!-- Each block with iteration count (aka "i") -->
<ul>
	{#each cats as { id, name }, i}
		<li>
			<a target="_blank" rel="noreferrer" href="https://www.youtube.com/watch?v={id}">
				{i + 1}: {name}
			</a>
		</li>
	{/each}
</ul>

<!-- Each block with only partial data -->
<ul>
	{#each cats as { name }}
		<li>
			{name}
		</li>
	{/each}
</ul>

<!-- Each block with only partial data, plus iteration count -->
<ul>
	{#each cats as { name }, i}
		<li>
			{i + 1}: {name}
		</li>
	{/each}
</ul>