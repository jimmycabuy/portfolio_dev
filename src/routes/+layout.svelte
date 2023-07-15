<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import Mouse from "../components/Mouse.svelte";
  import Background from "../components/Background.svelte";
  import Loader from "../components/Loader.svelte";
  import "../app.css";
  let isLoading = true;

  setTimeout(() => {
    isLoading = false;
  }, 2500);
</script>

<div class="flex flex-col text-white sm:min-h-screen">
  {#if isLoading}
    <Loader />
    <Background />
  {:else}
    <Navbar />
    <slot />
    <Footer />
    <Mouse />
    <Background />
  {/if}
</div>
