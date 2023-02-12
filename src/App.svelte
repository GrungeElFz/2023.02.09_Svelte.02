<script>
  import ToDoList from "./lib/ToDoList.svelte";
  import { v4 as uuid } from 'uuid';

  const toDoLists = [
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
</script>

<ToDoList {toDoLists} />

<style>

</style>