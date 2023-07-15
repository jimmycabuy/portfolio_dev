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

{#if isLoading}
  <Loader />
{:else}
  <div class="flex flex-col text-white sm:min-h-screen">
    <Navbar />
    <slot />
    <Footer />
    <Mouse />
    <Background />
  </div>
{/if}
