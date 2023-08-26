<script>
  import Skills from "./Skills.svelte";
  const banner = "/assets/banner.webp";
  const pdf = "/document/jimmy_cabuy_resume.pdf";
  import { blur } from "svelte/transition";
</script>

<svelte:head>
  <title>Jimmy C. | Web Developer.</title>
</svelte:head>

<main class="flex justify-center items-center py-6 px-12 4xl:px-72" in:blur>
  <div class="container_home flex justify-center items-center">
    <div class="profile-container max-w-[75%]">
      <div class="flex flex-col gap-6 items-start md:items-center">
        <div />
        <h1 class="text-7xl">Jimmy Cabuy</h1>
        <div class="flex gap-2 flex-col md:flex-row">
          <h2 class="text-md sm:text-xl">Front-end developer & Photographer</h2>
        </div>
        <p class="text-center">
          Hi! I'm Jimmy, a versatile full-stack developer, designer, and
          photographer with a degree in e-business. I have 2+ years of digital
          marketing experience, specializing in content creation and social
          media management. After a 6-month photography adventure, I completed a
          JavaScript Bootcamp and now work as a front-end developer at
          Decathlon. I'm a curious and creative professional always seeking new
          challenges.
        </p>
        <!-- <Skills /> -->
        <a href={pdf} target="_blank" rel="noopener noreferrer">
          <span class="flex">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="3 0 24 16"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-5 h-5"
              color="#a1a1a1"
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

  h1 {
    font-family: "DeeDee-Bold", sans-serif;
  }

  p {
    color: #a1a1a1;
  }

  a {
    position: relative;
    text-decoration: none;
    color: #a1a1a1;
    width: fit-content;
  }

  @media (min-width: 1023px) {
    a::after {
      content: "";
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 0;
      height: 2px;
      background-color: #a1a1a1;
      transition: width 0.3s ease-in-out;
    }

    a:hover::after {
      width: 100%;
    }
  }

  @media (max-width: 767px) {
    h1 {
      font-size: xxx-large;
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

    p {
      text-align: justify;
    }
  }
</style>
