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
			toDoLists.push({
			id: uuid(),
			title: event.detail.title,
			completed: false
		});

		/*
		• toDoLists is assigned to itself in order to trigger a reactivity update in the Svelte component.
		• When a new task is added to the toDoLists array, the component needs to know that the array has been updated and should re-render with the new data.
		• By assigning toDoLists to itself, Svelte is able to detect the change and update the component accordingly.
		*/
		toDoLists = toDoLists;
	};
</script>

<h2>{toDoLists.length} Tasks</h2>
<ToDoList {toDoLists} on:addtodo={handleToDoLists} />

<style>
</style>
