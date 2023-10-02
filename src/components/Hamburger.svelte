<script>
  export let open = false;
</script>

<button
  class="border-none focus:outline-none"
  class:open
  on:click={() => (open = !open)}
>
  <h2 class="text-2xl sm:text-3xl">
    {#if !open}
      MENU.
    {:else}
      CLOSE.
    {/if}
  </h2>
</button>

<style>
  button {
    z-index: 4;
  }

  h2 {
    font-variation-settings: "ital" 0, "wdth" 150, "wght" 800;
  }
</style>
