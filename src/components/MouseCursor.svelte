<script>
  import { onMount } from 'svelte';
  import { writable, get } from 'svelte/store';

  const x = writable(0);
  const y = writable(0);
  const smoothness = 0.2;
  let targetTagName = false;

  let mouseX = 0;
  let mouseY = 0;

  onMount(() => {
    window.addEventListener('mousemove', handleMouseMove);
    setInterval(updatePosition);
  });

  function handleMouseMove(event) {
    mouseX = event.clientX;
    mouseY = event.clientY;

    const targetElement = document.elementFromPoint(mouseX, mouseY);

    if (targetElement.classList.contains('enlarged')) {
      targetTagName = true;
    } else {
      targetTagName = false;
    }
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

<div class="custom-cursor" style="left: {$x - 10}px; top: {$y - 10}px;">
  <div class="dot" class:enlarged={targetTagName} />
</div>

<style>
  .custom-cursor {
    position: fixed;
    width: 20px;
    height: 20px;
    pointer-events: none;
    z-index: 10000;
    cursor: none;
  }

  .custom-cursor .dot {
    width: 10px;
    height: 10px;
    background-color: #fff;
    border-radius: 50%;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transition:
      transform 0.2s,
      width 0.2s,
      height 0.2s;
  }

  .custom-cursor .dot.enlarged {
    width: 60px;
    height: 60px;
    opacity: 0.5;
  }

  @media (pointer: coarse) {
    .custom-cursor {
      display: none;
    }
  }
</style>
