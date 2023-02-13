<script>
  export let toDoLists = [];
</script>

<ul>
  {#each toDoLists as { id, title }, index (id) }
    {@const number = index + 1}
    <li>{number}. {title}</li>
  {/each}
</ul>