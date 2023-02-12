<script>
  export let toDoLists = [];
</script>

<ul>
  {#each toDoLists as toDoList, index (toDoList.id) }
    {@const number = index + 1}
    <li>{number}. {toDoList.title}</li>
  {/each}
</ul>