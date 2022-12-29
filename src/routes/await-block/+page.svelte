<script>
	let x = getRandomNumber();

	async function getRandomNumber() {
		const response = await fetch(`http://localhost:3030/`);
		const text = await response.text();

		if (response.ok) {
			return text;
		} else {
			throw new Error(text);
		}
	}

	function handleClick() {
		x = getRandomNumber();
	}
</script>

<h1>Await Block</h1>

<button on:click={handleClick}>
	generate random number
</button>

<p>The number is {x}</p>

{#await x}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
