<script>
  export let open = false;
</script>

<button class="border-none focus:outline-none" on:click={() => (open = !open)}>
  <h2 class="enlarged text-2xl sm:text-3xl">{open ? "CLOSE." : "MENU."}</h2>
</button>

<style>
  button {
    z-index: 12;
    font-weight: 700;
  }
</style>
