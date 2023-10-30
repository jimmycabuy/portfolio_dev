<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import Mouse from "../components/Mouse.svelte";
  import Background from "../components/Background.svelte";
  import Loader from "../components/Loader.svelte";
  import "../app.css";
  import { page } from "$app/stores";
  import SidebarMenu from "../components/SidebarMenu.svelte";

  const isParamsInUrl = Object.keys($page.params).length !== 0;
  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 2500);

  let open = false;
</script>

<div class="flex flex-col text-white">
  {#if isLoading && !isParamsInUrl}
    <Loader />
  {:else}
    <SidebarMenu bind:open />
    <Navbar bind:sidebar={open} />
    <span class:open>
      <slot />
    </span>
    <span class:open>
      <Footer />
    </span>
    <Mouse />
    <Background />
  {/if}
</div>

<style>
  div {
    min-height: 100dvh;
    justify-content: space-between;
    max-width: 100vw;
  }

  span {
    max-width: 100vw;
  }

  .open {
    display: none;
  }
</style>
