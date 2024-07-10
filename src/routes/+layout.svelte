<script>
  import Navbar from '../components/Navbar.svelte';
  import Footer from '../components/Footer.svelte';
  import MouseFollower from '../components/MouseFollower.svelte';
  import MouseCursor from '../components/MouseCursor.svelte';
  import Background from '../components/Background.svelte';
  import Loader from '../components/Loader.svelte';
  import '../app.css';
  import { page } from '$app/stores';
  import SidebarMenu from '../components/SidebarMenu.svelte';

  let isLoading = true;
  let open = false;

  const isParamsInUrl = Object.keys($page.params).length !== 0;
  const isGallery = $page.route.id === '/gallery';

  setTimeout(() => {
    isLoading = false;
  }, 2500);
</script>

<div class="flex flex-col text-white" class:open>
  {#if isLoading && !isParamsInUrl && !isGallery}
    <Loader />
  {:else}
    <SidebarMenu bind:open />
    <Navbar bind:sidebar={open} />
    <slot />
    <Footer />
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

  .open {
    overflow: hidden;
    max-height: 100dvh;
  }
</style>
