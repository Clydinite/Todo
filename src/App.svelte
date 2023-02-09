<script>
  let todos = [
    { done: true, name: "Learn HTML" },
    { done: true, name: "Learn CSS" },
    { done: true, name: "Learn JavaScript" },
    { done: false, name: "Choose a front-end framework" },
    { done: false, name: "Write a hello world program in the framework" },
    { done: false, name: "Finish a todo list" },
  ];

  function addTodos() {
    todos.push({ done: false, name: "" });
    todos = todos; // reassign to refresh
  }

  function clear() {
    todos = todos.filter((t) => !t.done);
  }

  $: remaining = todos.filter((t) => !t.done).length;
</script>

<link
  href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@700&display=swap"
  rel="stylesheet"
/>
<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD"
  crossorigin="anonymous"
/>

<div class="container">
  <h3 class="text-center m-3">Path To Be a Front-End Developer</h3>
  <p>{remaining} task{remaining == 1 ? "" : "s"} remaining</p>

  {#each todos as todo}
    <div class="input-group mb-3">
      <div class="input-group-text">
        <input
          class="form-check-input mt-0"
          type="checkbox"
          bind:checked={todo.done}
        />
      </div>
      <input
        type="text"
        class="form-control"
        bind:value={todo.name}
        placeholder="What's on your mind?"
      />
    </div>
  {/each}

  <div class="d-grid gap-3">
    <button class="btn btn-outline-secondary" type="button" on:click={addTodos}
      >Add Task</button
    >
    <button class="btn btn-outline-secondary" type="button" on:click={clear}
      >Clear Completed</button
    >
  </div>
</div>

<style>
  * {
    font-family: "Jetbrains Mono";
  }
</style>
