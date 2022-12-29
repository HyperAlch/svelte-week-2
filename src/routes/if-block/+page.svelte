<script>
	let user = { 
        loggedIn: false,
        name: ""
    };

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

    // user.name = "Bob"
    // user.name = "Joe"
</script>

<h1>If Block</h1>

{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{/if}

{#if !user.loggedIn}
	<button on:click={toggle}>
		Log in
	</button>
{/if}

{#if user.name}
    <p>Username: { user.name }</p>
{/if}

{#if user.name === "Joe"}
    <p>Hello Joe!</p>
{/if}