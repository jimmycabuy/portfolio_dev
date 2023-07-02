<script>
  import { mail, share, github, instagram } from "../icons";
  const date = new Date()
  const year = date.getFullYear();
</script>

<footer
  class="bg-zinc-800 py-6 px-12 flex flex-row justify-between items-center"
>
  <div class="flex flex-row justify-start items-center gap-16">
    <div class="w-20 h-20 rounded-full overflow-hidden">
      <!-- svelte-ignore a11y-img-redundant-alt -->
      <img
        src="https://jimmycabuy.vercel.app/images/portrait.webp"
        alt="jimmy-cabuy-profile-picture"
        class="w-full h-full object-cover scale-125"
      />
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <span class="icon">{@html mail}</span>
      <span class="email_me text-xl text-zinc-400">Email me</span>
      <span class="mb-1 hover:cursor-pointer">
        <a href="mailto:jimmycabuy@hotmail.com" target="_blank">
          {@html share}
        </a>
      </span>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <span class="icon">{@html github}</span>
      <span class="email_me text-xl text-zinc-400">Github</span>
      <span class="mb-1 hover:cursor-pointer">
        <a href="https://github.com/jimmycabuy" target="_blank">
          {@html share}
        </a>
      </span>
    </div>
    <div class="flex flex-row justify-between gap-1 items-end">
      <span class="icon">{@html instagram}</span>
      <span class="email_me text-xl text-zinc-400">Instagram</span>
      <span class="mb-1 hover:cursor-pointer">
        <a href="https://instagram.com/jimmycabuy" target="_blank">
          {@html share}
        </a>
      </span>
    </div>
    <div />
  </div>
  <div>
    <p class="text-zinc-400">Designed and coded by Jimmy © {year}</p>
  </div>
</footer>

<style>
  footer {
    height: 15vh;
    max-height: 15vh;
  }
  .email_me {
    margin-bottom: -0.259rem;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  .icon {
    margin-bottom: 0.085rem;
  }
</style>
