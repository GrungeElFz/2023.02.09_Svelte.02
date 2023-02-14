<script>
	import { v4 as uuid } from 'uuid';
	export let toDoLists = [];

	let inputText = '';
	function handleToDoLists() {
		toDoLists = toDoLists;

		if (!inputText) return;
		toDoLists = [
			...toDoLists,
			{
				id: uuid(),
				title: inputText,
				completed: false
			}
		];

		inputText = '';
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
		<button type="submit" disabled={!inputText}>Add</button>
	</form>
</div>
