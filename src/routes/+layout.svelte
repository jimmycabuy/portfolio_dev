<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import Mouse from "../components/Mouse.svelte";
  import Background from "../components/Background.svelte";
  import "../app.css";
</script>

<div class="flex flex-col text-white sm:min-h-screen">
  <Navbar />
  <slot />
  <Footer />
  <Mouse />
  <Background />
</div>