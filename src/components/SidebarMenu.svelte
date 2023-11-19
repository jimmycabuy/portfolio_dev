<script>
  import menu from "../data/menu.json";
  import gsap from "gsap";

  export let open = false;

  function closeSidebar() {
    setTimeout(() => {
      open = false;
    }, 350);
  }

  $: if (open) {
    gsap.from(".one_menu_item", {
      y: 30,
      duration: 0.6,
      delay: 0.3,
      opacity: 0,
      stagger: 0.2,
    });
  }
</script>

<aside class="absolute bg-black" class:open>
  <nav class="text-4xl md:text-5xl">
    {#each menu as item, i}
      {#if item?.isActive}
        <div class="enlarged one_menu_item">
          <small class="text-sm">0{i + 1}</small>
          <a
            href={item?.link}
            on:click={closeSidebar}
            data-sveltekit-preload-data
            data-sveltekit-preload-code
            class="enlarged"
          >
            {item?.label}
          </a>
        </div>
      {/if}
    {/each}
  </nav>
</aside>

<style>
  aside {
    z-index: 3;
    left: -100%;
    transition: left 0.3s ease-in-out;
    min-height: 100dvh;
    min-width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  nav {
    display: flex;
    flex-direction: column;
    gap: 3rem;
  }

  .open {
    left: 0;
  }

  a {
    text-decoration: none;
    -webkit-text-stroke: 1px #fff;
    color: transparent;
    text-transform: uppercase;
    font-weight: 700;
    position: relative;
  }

  @media (pointer: fine) {
    a::before {
      background: #ff2f66;
      content: "";
      inset: 0;
      position: absolute;
      transform: scaleX(0);
      transform-origin: right;
      transition: transform 0.5s ease-in-out;
      z-index: -1;
    }

    a:hover::before {
      transform: scaleX(1);
      transform-origin: left;
    }

    a:hover {
      color: #fff;
      transition: 0.5s;
    }
  }
</style>
