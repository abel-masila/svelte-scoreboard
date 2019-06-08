<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "John Doe",
      points: 53
    },
    {
      name: "Sam Smith",
      points: 45
    },
    {
      name: "Sara Wilson",
      points: 34
    }
  ];
  const addplayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };
  const removePlayer = e => {
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addplayer} />
  {#if players.length === 0}
    <p>No players</p>
  {:else}
    {#each players as player}
      <Player
        name={player.name}
        points={player.points}
        on:removeplayer={removePlayer} />
    {/each}
  {/if}
</div>
