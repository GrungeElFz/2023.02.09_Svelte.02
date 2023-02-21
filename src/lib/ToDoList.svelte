<script>
	import Button from './Button.svelte';
	import { createEventDispatcher } from "svelte";

	export let toDoLists = [];
	let inputText = '';
	const dispatch = createEventDispatcher();

	function handleToDoLists() {
		const isNotCancelled = dispatch(
			'addtodo', 
			{title: inputText},
			{cancelable: true}
		);
		
		if (isNotCancelled) {
			inputText = '';
			// console.log('Backfired');
		};
	}
</script>

<div class="toDoLists-wrapper">
	<ul>
		{#each toDoLists as { id, title }, index (id)}
			{@const number = index + 1}
			<li>{number}. {title}</li>
		{/each}
	</ul>

	<form class="toDoLists-form" on:submit|preventDefault={handleToDoLists}>
		<input bind:value={inputText} />
		<Button type="submit" disabled={!inputText}>Add</Button>
	</form>
</div>
