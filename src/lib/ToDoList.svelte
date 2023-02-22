<svelte:options immutable={true} />

<script>
	import Button from './Button.svelte';
	import { createEventDispatcher } from 'svelte';

	export let toDoLists = [];
	let inputText = '';
	const dispatch = createEventDispatcher();

	function handleToDoLists() {
		const isNotCancelled = dispatch('addtodo', { title: inputText }, { cancelable: true });

		if (isNotCancelled) {
			inputText = '';
		}
	}

	function handleRemoveToDoLists(id) {
		dispatch('removetodo', {
			id
		});
	}
</script>

<div class="toDoLists-wrapper">
	<ul>
		{#each toDoLists as { id, title, completed } (id)}
			<li>
				<label>
					<input type="checkbox" checked={completed} />
					{title}
				</label>
				<button on:click={() => handleRemoveToDoLists(id)}>Remove</button>
			</li>
		{/each}
	</ul>

	<form class="toDoLists-form" on:submit|preventDefault={handleToDoLists}>
		<input bind:value={inputText} />
		<Button type="submit" disabled={!inputText}>Add</Button>
	</form>
</div>