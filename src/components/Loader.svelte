<script>
  import Background from "./Background.svelte";
  import { onMount } from "svelte";
  onMount(() => {
    var loadingDiv = document.querySelector(".loader");
    loadingDiv.style.opacity = "0";
    loadingDiv.style.filter = "blur(6px)";
    setTimeout(function () {
      loadingDiv.style.transition = "opacity 0.3s, filter 0.3s";
      loadingDiv.style.opacity = "1";
      loadingDiv.style.filter = "blur(0)";
    }, 500);
    setTimeout(function () {
      var loadingDiv = document.querySelector(".loader");
      loadingDiv.style.filter = "blur(6px)";
    }, 2200);
    setTimeout(function () {
      var loadingDiv = document.querySelector(".loader");
      loadingDiv.style.opacity = "0";
    }, 2400);
  });
</script>

<div class="loading">
  <span class="loader" />
</div>
<Background />

<style>
  .loading {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    max-height: 100vh;
    z-index: 1;
    overflow: hidden;
  }

  .loader {
    width: 100px;
    height: 100px;
    background-color: #bbb;
    border-radius: 50%;
    position: relative;
    box-shadow: 0 0 30px 4px rgba(0, 0, 0, 0.5) inset,
      0 5px 12px rgba(0, 0, 0, 0.15);
    overflow: hidden;
    opacity: 0;
    filter: blur(6px);
    transition: opacity 0.5s, filter 0.5s;
  }
  .loader:before,
  .loader:after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 45%;
    top: -40%;
    background-color: #fff;
    animation: wave 4s linear infinite;
  }
  .loader:before {
    border-radius: 30%;
    background: rgba(255, 255, 255, 0.4);
    animation: wave 4s linear infinite;
  }
  @keyframes wave {
    0% {
      transform: rotate(0);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  @media (max-width: 1100px) {
    .loading {
      min-height: calc(100vh - 100px);
      max-height: 100vh;
    }
    .loader {
      width: 70px;
      height: 70px;
    }
  }
</style>
