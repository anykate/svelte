<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    // {
    //   name: "John Doe",
    //   points: 53
    // },
    // {
    //   name: "Aniket Aryamane",
    //   points: 100
    // },
    // {
    //   name: "Brad Traversy",
    //   points: 45
    // }
  ];

  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const deletePlayer = e => {
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<style>
  h3 {
    color: red;
  }
</style>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <h3>No players found!</h3>
  {:else}
    {#each players as player, i}
      <Player
        name={player.name}
        points={player.points}
        on:deleteplayer={deletePlayer} />
    {/each}
  {/if}
</div>
