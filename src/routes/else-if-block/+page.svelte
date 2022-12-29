<script>
	let x = 0;

	function gen_random_number(low, high) {
		// Generate a number between low - high
		return Math.floor(Math.random() * high) + low
	}

	function button_clicked() {
		let new_x = gen_random_number(1, 12)

		// Make sure the number generated isn't the exact same as the original
		if (new_x === x) {
			button_clicked()
		} else {
			x = new_x
		}
	}
</script>

<h1>Else If Block</h1>
<button on:click={button_clicked}>
	Generate New Number
</button>

{#if x > 10}
	<p>{x} is greater than 10</p>
{:else if 5 > x}
	<p>{x} is less than 5</p>
{:else}
	<p>{x} is between 5 and 10</p>
{/if}