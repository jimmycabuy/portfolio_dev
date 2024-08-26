<script>
  import socials from '../data/socials';
  const date = new Date();
  const year = date.getFullYear();
</script>

<footer class="py-6 px-12 flex flex-row justify-between items-center 4xl:px-72">
  <div class="block_left_home flex flex-row justify-start items-center gap-8">
    {#each socials as { label, href, target, icon }}
      <div class="enlarged flex flex-row justify-between gap-1 items-end">
        <a class="enlarged flex items-center" {href} {target}>
          <span class="icon enlarged">{@html icon}</span>
          <span class="enlarged link_footer_name text-md">{label}</span>
        </a>
      </div>
    {/each}
  </div>
  <div class="block_right_home">
    <p>Designed and coded by me © {year}</p>
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

  .block_left_home,
  .block_right_home {
    z-index: 2;
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
