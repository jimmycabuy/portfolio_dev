<script>
  import Skills from "./Skills.svelte";
  import { blur } from "svelte/transition";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  const pdf = "/document/jimmy_cabuy_resume.pdf";
  const banner = "/assets/banner.webp";

  let main;

  $: if (main) {
    gsap.from(".my_name", {
      y: -100,
      duration: 0.8,
      delay: 0.5,
      opacity: 0,
    });

    gsap.from(".my_title, .my_description, .my_resume", {
      duration: 3,
      delay: 0.8,
      opacity: 0,
    });
  }
  onMount(() => {
    main = document.querySelector("main");
  });
</script>

<svelte:head>
  <title>Jimmy C. | Web Developer.</title>
</svelte:head>

<main
  class="flex justify-center items-center py-6 px-6 md:px-12 4xl:px-72"
  in:blur
>
  <div class="container_home flex justify-center items-center">
    <div class="profile-container max-w-[75%]">
      <div class="flex flex-col gap-8 items-center text-center">
        <h1 class="my_name text-4xl sm:text-5xl md:text-7xl">Jimmy Cabuy</h1>
        <div class="flex gap-2 flex-col md:flex-row">
          <h2 class="my_title text-xl sm:text-2xl">
            Front-end developer & Photographer
          </h2>
        </div>
        <p class="my_description text-center leading-6">
          I'm Jimmy, a full-stack developer, designer, and photographer with
          digital marketing experience. After a global photography journey, I
          became a front-end developer at Decathlon, always seeking new
          challenges.
        </p>
        <!-- <Skills /> -->
        <a
          href={pdf}
          target="_blank"
          rel="noopener noreferrer"
          class="my_resume animate-bounce"
        >
          <span class="flex">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="3 0 24 16"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-5 h-5"
              color="#fff"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M12 4.5v15m0 0l6.75-6.75M12 19.5l-6.75-6.75"
              />
            </svg>
            <p class="text-lg">My resume.</p>
          </span>
        </a>
      </div>
    </div>
  </div>
</main>

<style>
  main {
    overflow: hidden;
    z-index: 1;
  }

  p {
    color: #fff;
  }

  h1 {
    text-transform: uppercase;
    font-weight: 700;
    position: relative;
    white-space: nowrap;
  }

  h1:after {
    --deco-height: 0.3125em;
    content: "";
    position: absolute;
    left: 0;
    right: 0;
    bottom: calc(var(--deco-height) * -0.625);
    height: var(--deco-height);
    background-image: url("data:image/svg+xml,%3Csvg width='100' height='64' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg clip-path='url(%23a)'%3E%3Cpath d='M-17 30.5C-1 22 72-4 54 13 37.9 28.2-2.5 57.5 16 55.5s72-29 104-40' stroke='%23FF2F66' stroke-width='10'/%3E%3C/g%3E%3Cdefs%3E%3CclipPath id='a'%3E%3Cpath fill='%23fff' d='M0 0h100v64H0z'/%3E%3C/clipPath%3E%3C/defs%3E%3C/svg%3E%0A");
    background-size: auto 100%;
    background-repeat: round;
    background-position: 0em;
  }

  a {
    position: relative;
    text-decoration: none;
    color: #fff;
    width: fit-content;
  }

  @media (pointer: fine) {
    a::after {
      content: "";
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 0;
      height: 2px;
      background-color: #fff;
      transition: width 0.3s ease-in-out;
    }

    a:hover::after {
      width: 100%;
    }
  }

  @media (max-width: 1023px) {
    main {
      max-height: fit-content;
    }
    .container_home {
      height: fit-content;
      flex-direction: column;
    }

    .profile-container {
      max-width: 100%;
    }
  }
</style>
