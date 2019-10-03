<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let name, points;
  let showControls = false;

  const addPoints = () => (points += 1);
  const subPoints = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);

  const onDelete = () => dispatch("deleteplayer", name);
</script>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggleControls}>
      {#if !showControls}+{:else}-{/if}
    </button>
    <button class="btn btn-danger btn-sm" on:click={onDelete}>x</button>
  </h1>
  <h3>Points: {points}</h3>
  {#if showControls}
    <!-- content here -->
    <button class="btn btn-sm" on:click={addPoints}>+1</button>
    <button class="btn btn-sm btn-dark" on:click={subPoints}>-1</button>
    <input type="number" name="points" id="points" bind:value={points} />
  {/if}
</div>
