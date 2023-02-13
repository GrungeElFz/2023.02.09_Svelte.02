<script>
	export let toDoLists = [];
</script>

<div class="toDoLists-wrapper">
	<ul>
		{#each toDoLists as { id, title }, index (id)}
			{@const number = index + 1}
			<li>{number}. {title}</li>
		{/each}
	</ul>

	<form class="toDoLists-form">
		<input />
		<button type="submit">Add</button>
	</form>
</div>
