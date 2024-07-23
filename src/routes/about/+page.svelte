<script>
	let newItem = '';
	let todoList = [
		{ text: 'first post', status: true },
		{ text: 'upload the dog', status: false },
		{ text: 'publish the post', status: false }
	];

	function addTodo() {
		todoList = [...todoList, { text: newItem, status: false }];
		newItem = '';
	}

	function removeFromList(index) {
		todoList.splice(index, 1);
		todoList = todoList;
	}
</script>

<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<h1>About this app</h1>

<input bind:value={newItem} type="text" placeholder="new todo item.." />
<button on:click={addTodo}>Add</button>

<br />
{#each todoList as item, index}
	<input bind:checked={item.status} type="checkbox" />
	<span class:checked={item.status}>{item.text}</span>
	<span on:click={() => removeFromList(index)}>❌</span>
	<br />
{/each}

<style>
	.checked {
		text-decoration: line-through;
	}
</style>
