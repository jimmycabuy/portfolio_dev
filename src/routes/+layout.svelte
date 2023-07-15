<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import Mouse from "../components/Mouse.svelte";
  import Background from "../components/Background.svelte";
  import Loader from "../components/Loader.svelte";
  import "../app.css";
  import { page } from "$app/stores";

  const isParamsInUrl = Object.keys($page.params).length !== 0;
  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 2500);
</script>

<div class="flex flex-col text-white sm:min-h-screen">
  {#if isLoading && !isParamsInUrl}
    <Loader />
  {:else}
    <Navbar />
    <slot />
    <Footer />
    <Mouse />
    <Background />
  {/if}
</div>
