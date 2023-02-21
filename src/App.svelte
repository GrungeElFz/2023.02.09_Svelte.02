<script>
	import ToDoList from './lib/ToDoList.svelte';
	import { v4 as uuid } from 'uuid';

	let toDoLists = [
		{
			id: uuid(),
			title: 'First task',
			completed: true
		},
		{
			id: uuid(),
			title: 'Second task',
			completed: false
		},
		{
			id: uuid(),
			title: 'Third task',
			completed: false
		}
	];

	function handleToDoLists(event) {
		event.preventDefault;
		// console.log(event.detail.title);
	};
</script>

<h2>{toDoLists.length} Tasks</h2>
<ToDoList {toDoLists}
	on:addtodo={handleToDoLists}
/>

<style>
</style>
