<script>
  import { fade, fly } from "svelte/transition";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function remove() {
    dispatch("remove", { id });
  }

  function toggleStatus() {
    let newStatus = !complete;
    dispatch("toggle", {
      id,
      newStatus,
    });
  }

  export let id, text, complete;
</script>

<li in:fly={{ x: 900, duration: 500 }}>
  <span class:complete>
    {text}
  </span>

  {#if complete}
    <button on:click={toggleStatus}> check </button>
  {:else}
    <button on:click={toggleStatus}> x </button>
  {/if}
</li>

<style>
  .complete {
    text-decoration: line-through;
    color: green;
  }
</style>
