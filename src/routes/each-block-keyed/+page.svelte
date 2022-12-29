<script>
	import Thing from './Thing.svelte';

	let things = [
		{ name: 'apple' },
		{ name: 'banana' },
		{ name: 'carrot' },
		{ name: 'doughnut' },
		{ name: 'egg' },
	];

    let things_keyed = [
		{ id: 0, name: 'apple' },
		{ id: 1, name: 'banana' },
		{ id: 2, name: 'carrot' },
		{ id: 3, name: 'doughnut' },
		{ id: 4, name: 'egg' },
	];

	function handleClick(event) {
        event = event.target.id
        if (event === "things") things = things.slice(1)
        else if (event === "things-keyed") things_keyed = things_keyed.slice(1)
        else console.error("Unknown click event")
	}
</script>

<h1>Each Block Keyed</h1>

<!-- Components are refreshed in different ways -->

<!-- Properties are refreshed automatically when the parent changes them. However, this does not refresh the component as a whole -->
<!-- One way to force a component refresh in the case of an each block is to change the ID of the component -->
<h3>Things</h3>
<button id="things" on:click={handleClick}>
	Remove thing
</button>
<br><br>
<!-- Normally the ID of a component displayed via an each block is bound to the array index -->
<!-- However, this can cause some issues because of the default way JavaScript handles arrays. -->
<!-- Array index's change automatically based on the arrays length... -->
{#each things as thing, i}
	{i}<Thing name={thing.name}/>
{/each}

<br><br><br>

<h3>Things Keyed</h3>
<button id="things-keyed" on:click={handleClick}>
	Remove thing
</button>
<br><br>
<!-- Here we give each item in our array a custom ID that will not change, even when we change the array -->

{#each things_keyed as thing (thing.id)}
	{thing.id}<Thing name={thing.name}/>
{/each}

<!-- 
    [None-Keyed]
        0 -> 0
        1 -> 1
        2 -> 2
        3 -> 3
        4 -> 4
    * Deleted an item * (JavaScript recalculates the array index's, which are also our id's)
        0 -> 0
        1 -> 1
        2 -> 2
        3 -> 3
    The id's for 0 - 3 have not changed, no refresh happens (other than the property)


    [Keyed]
        0 -> 0
        1 -> 1
        2 -> 2
        3 -> 3
        4 -> 4
    * Deleted an item *
        1 -> 1
        2 -> 2
        3 -> 3
        4 -> 4
    The id's in the set HAVE changed, svelte refreshes all the components in the each block

 -->