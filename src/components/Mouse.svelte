<script>
  import { onMount } from "svelte";
  import { writable, get } from "svelte/store";

  const x = writable(0);
  const y = writable(0);
  const smoothness = 0.2;
  const delay = 20;

  let mouseX = 0;
  let mouseY = 0;

  onMount(() => {
    window.addEventListener("mousemove", handleMouseMove);
    setInterval(updatePosition, delay);
  });

  function handleMouseMove(event) {
    mouseX = event.clientX;
    mouseY = event.clientY;
  }

  function updatePosition() {
    const targetX = get(x);
    const targetY = get(y);

    const dx = (mouseX - targetX) * smoothness;
    const dy = (mouseY - targetY) * smoothness;

    x.set(targetX + dx);
    y.set(targetY + dy);
  }
</script>

<div class="mouse-follower" style="left: {$x - 10}px; top: {$y - 10}px;">
  <div class="dot" />
</div>

<style>
  .mouse-follower {
    position: fixed;
    width: 20px;
    height: 20px;
    border: 2px solid #a1a1a1;
    border-radius: 50%;
    pointer-events: none;
    background: none;
    z-index: 1;
  }

  .mouse-follower .dot {
    position: absolute;
    width: 3px;
    height: 3px;
    background-color: #a1a1a1;
    border-radius: 50%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  @media (max-width: 1023px) {
    .mouse-follower {
      display: none;
    }
  }
</style>
