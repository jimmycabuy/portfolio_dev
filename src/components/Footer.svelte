<script>
  import { mail, share, github, instagram } from "../icons";
  const date = new Date();
  const year = date.getFullYear();
</script>

<footer class="py-6 px-12 flex flex-row justify-between items-center">
  <div class="block_left_home flex flex-row justify-start items-center gap-8">
    <!-- <div class="w-20 h-20 rounded-full overflow-hidden">
      <img
        src="https://jimmycabuy.vercel.app/images/portrait.webp"
        alt="jimmy-cabuy-profile-picture"
        class="w-full h-full object-cover scale-125"
      />
    </div> -->
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="mailto:jimmycabuy@hotmail.com"
        target="_blank"
      >
        <span class="icon">{@html mail}</span>
        <span class="email_me text-md text-zinc-400">Email me</span>
        <span class="share mb-1 hover:cursor-pointer">
          <!-- {@html share} -->
        </span>
      </a>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="https://github.com/jimmycabuy"
        target="_blank"
      >
        <span class="icon">{@html github}</span>
        <span class="email_me text-md text-zinc-400">Github</span>
        <span class="share mb-1 hover:cursor-pointer">
          <!-- {@html share} -->
        </span>
      </a>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <a
        class="flex items-center"
        href="https://instagram.com/jimmycabuy"
        target="_blank"
      >
        <span class="icon">{@html instagram}</span>
        <span class="email_me text-md text-zinc-400">Instagram</span>
        <span class="share mb-1 hover:cursor-pointer">
          <!-- {@html share} -->
        </span>
      </a>
    </div>
  </div>
  <div>
    <p class="text-zinc-400">Designed and coded by Jimmy © {year}</p>
  </div>
</footer>

<style>
  footer {
    height: 10vh;
    max-height: 10vh;
    z-index: 1;
  }
  .email_me {
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
    .email_me {
      font-size: large;
    }
    footer {
      gap: 3rem;
      height: fit-content;
      max-height: fit-content;
    }
    footer,
    .block_left_home {
      flex-direction: column;
    }

    .block_left_home {
      gap: 0;
    }

    .icon,
    .share {
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
