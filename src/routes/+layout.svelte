<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import MouseFollower from "../components/MouseFollower.svelte";
  import MouseCursor from "../components/MouseCursor.svelte";
  import Background from "../components/Background.svelte";
  import Loader from "../components/Loader.svelte";
  import "../app.css";
  import { page } from "$app/stores";
  import SidebarMenu from "../components/SidebarMenu.svelte";

  let isLoading = true;

  const isParamsInUrl = Object.keys($page.params).length !== 0;
  const isGallery = $page.route.id === "/gallery";

  setTimeout(() => {
    isLoading = false;
  }, 2500);

  let open = false;
</script>

<div class="flex flex-col text-white">
  {#if isLoading && !isParamsInUrl && !isGallery}
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
    <MouseCursor />
    <MouseFollower />
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
