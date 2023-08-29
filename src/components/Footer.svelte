<script>
  import { mail, github, instagram, linkedin } from "../icons";
  const date = new Date();
  const year = date.getFullYear();
</script>

<footer class="py-6 px-12 flex flex-row justify-between items-center 4xl:px-72">
  <div class="block_left_home flex flex-row justify-start items-center gap-8">
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="mailto:jimmycabuy@hotmail.com"
        target="_blank"
      >
        <span class="icon">{@html mail}</span>
        <span class="link_footer_name text-md">Email me</span>
        <span class="share mb-1 hover:cursor-pointer" />
      </a>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="https://github.com/jimmycabuy"
        target="_blank"
      >
        <span class="icon">{@html github}</span>
        <span class="link_footer_name text-md">Github</span>
        <span class="share mb-1 hover:cursor-pointer" />
      </a>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="https://linkedin.com/in/jimmycabuy"
        target="_blank"
      >
        <span class="icon">{@html linkedin}</span>
        <span class="link_footer_name text-md">LinkedIn</span>
        <span class="share mb-1 hover:cursor-pointer" />
      </a>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="https://instagram.com/jimmycabuy"
        target="_blank"
      >
        <span class="icon">{@html instagram}</span>
        <span class="link_footer_name text-md">Instagram</span>
        <span class="share mb-1 hover:cursor-pointer" />
      </a>
    </div>
  </div>
  <div>
    <p class="">Designed and coded by Jimmy © {year}</p>
  </div>
</footer>

<style>
  footer {
    height: 10vh;
    max-height: 10vh;
    z-index: 1;
  }
  .link_footer_name {
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  .icon {
    margin-bottom: 0.2rem;
  }

  /* Media Queries*/

  /* smartphone  */
  @media (max-width: 767px) {
    p {
      font-size: smaller;
    }
  }
  /* tablet  */
  @media (max-width: 1023px) {
    footer {
      gap: 3rem;
      height: fit-content;
      max-height: fit-content;
      flex-direction: column;
    }

    .link_footer_name {
      display: none;
    }
  }
  /* computer  */
  @media (min-width: 1024px) and (max-width: 2000px) {
  }
  /* big monitor  */
  @media (min-width: 2000px) {
  }
</style>
