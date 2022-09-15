<svelte:head>
  <title>todo list</title>
</svelte:head>

<script>
  let todoList = [
    { title: "example-1", done: false },
    { title: "example-2", done: false },
    { title: "example-3", done: true },
  ];
  let getError = "";
  let input = "";
  function addTodolist() {
    // @ts-ignore
    if (todoList.filter(value => value.title === input).length > 0 || input.length < 1) {
      getError = "Can not add todolist"
      return 0;
    }
    todoList = [
      ...todoList,
      {
        title: input,
        done: false,
      },
    ];
  }
  /**
   * @param {string} title_del
   */
  function removeTodolist(title_del) {
    todoList = todoList.filter((value) => value.title !== title_del);
  }
</script>

<div class="bg-gray-100 p-10 my-10 text-lg text-center rounded-md shadow-lg">
  <div class="text-rose-600">{getError}</div>
  <div>
    <input
      class="bg-white shadow-lg rounded focus:outline-blue-300 hover:border-blue-300 border-2 transition-all p-1"
      type="text"
      bind:value={input}
    />
    <button class="m-1 border-2 shadow-lg py-1 px-2 bg-white rounded hover:text-slate-600 hover:border-blue-300 transition-all focus:outline-blue-300" on:click={addTodolist}>add</button>
  </div>
  {#each todoList as list}
    <div>
      <input
      class="scale-150 m-2"
        type="checkbox"
        bind:checked={list.done}
      />
      {#if list.done}
        <strike class="text-slate-400">
          {list.title}
        </strike>
      {:else}
        {list.title}
      {/if}
      <span
        class="mx-1 text-red-500 cursor-pointer"
        on:click={() => removeTodolist(list.title)}>x</span
      >
    </div>
  {/each}
</div>
