<script lang="ts">
  let todos = [
    {done: false, text: 'お酒'},
    {done: false, text: 'バナナ'},
    {done: false, text: 'みりん'},
  ];

  const clear = () => {
    todos = todos.filter(e => !e.done);
  }
  const addNew = () => {
    todos = [...todos, {done: false, text: ''}];
  }

  $: remaining = todos.filter(e => !e.done).length;
</script>

{#each todos as todo}
  <div class:done={todo.done}>
    <ul class="todo">
      <li class="todo-item">
        <input type="checkbox" bind:checked={todo.done} />
        <input bind:value={todo.text} />
      </li>
    <ul>
  </div>
{/each}

<div>remining: {remaining} count</div>
<div>
  <button on:click={addNew}>new</button>
  <button on:click={clear}>clear</button>
</div>

<style lang="scss">
  .todo {
    margin-top: 0px;
    margin-bottom: 8px;
    padding: 0;
  }

  .todo-item {
    list-style:  none;
    padding: 0;

    input[type=checkbox] {
      margin-left: 0px;
    }
  }

  .done {
    opacity: 0.5;
  }
</style>
