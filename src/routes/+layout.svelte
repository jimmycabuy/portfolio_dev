<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import Mouse from "../components/Mouse.svelte";
  import "../app.css";
</script>

<div class="flex flex-col min-h-screen text-white">
  <Navbar />
  <slot />
  <Footer />
  <Mouse />
</div>