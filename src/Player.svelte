<script>
  export let name;
  export let points;
  let showControl = false;

  const addPoint = () => {
    points += 1;
  };
  const removePoint = () => {
    points -= 1;
  };
  const toggleControls = () => {
    showControl = !showControl;
  };
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
      {#if showControl}-{:else}+{/if}
    </button>
  </h1>
  <h3>Points : {points}</h3>
  {#if showControl}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>

    <input type="number" bind:value={points} />
  {/if}
</div>
