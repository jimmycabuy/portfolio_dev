<script>
  import Hamburger from "./Hamburger.svelte";
  export let sidebar = false;

  function toggleSidebar() {
    sidebar = !sidebar;
  }
</script>

<nav
  class="py-6 px-12 flex flex-row justify-between items-center text-white 4xl:px-72"
>
  <h2 class="enlarged text-2xl sm:text-3xl">
    <a href="/" class="enlarged">JIMMY.</a>
  </h2>
  <Hamburger bind:open={sidebar} on:click={toggleSidebar} />
</nav>

<style>
  nav {
    height: 10vh;
    max-height: 10vh;
  }

  h2 {
    z-index: 2;
  }

  a {
    font-weight: 700;
  }

  @media (max-width: 767px) {
  }
</style>
