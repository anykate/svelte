<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let player = {
    name: "",
    points: 0
  };

  const onSubmit = e => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = {
      name: "",
      points: 0
    };
  };
</script>

<form on:submit={onSubmit} class="grid-3">
  <input
    type="text"
    name="name"
    id="name"
    placeholder="Player Name"
    bind:value={player.name} />
  <input
    type="number"
    name="points"
    id="points"
    placeholder="Points"
    bind:value={player.points} />
  {#if player.name.length >= 1}
    <!-- content here -->
    <!-- <button type="submit" class="btn btn-primary btn-sm">Add Player</button> -->
    <input type="submit" class="btn btn-primary" value="Add Player" />
  {/if}
</form>
