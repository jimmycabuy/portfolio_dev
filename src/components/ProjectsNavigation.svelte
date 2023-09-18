<script>
  export let prevProject, nextProject;
</script>

<div class="container_navigation">
  <a
    href="/projects/{prevProject.route}"
    style="display: inline-flex; gap:5px"
    data-sveltekit-preload-code
    data-sveltekit-reload
    data-sveltekit-prefetch
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="currentColor"
      class="w-5 h-5"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18"
      />
    </svg>
    {prevProject.title}
  </a>
  <a
    href="/projects/{nextProject.route}"
    style="display: inline-flex; gap:5px"
    data-sveltekit-preload-code
    data-sveltekit-reload
    data-sveltekit-prefetch
  >
    {nextProject.title}
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="currentColor"
      class="w-5 h-5"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"
      />
    </svg>
  </a>
</div>

<style>
  a {
    position: relative;
    text-decoration: none;
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

  .container_navigation {
    width: 75%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 2rem;
  }

  @media (max-width: 1023px) {
    .container_navigation {
      width: 100%;
    }
  }
</style>
