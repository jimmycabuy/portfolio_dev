<svelte:head>
  <title>Jimmy C. | About me.</title>
</svelte:head>

<main class="flex justify-center flex-col items-center">
  <div>
    <h1 class="text-5xl md:text-7xl px-12 py-6">I'm Jimmy.</h1>
  </div>
  <div class="flex gap-10 px-10 xl:px-36 py-6 flex-col lg:flex-row">
    <div class="w-full lg:w-1/2">
      <img
        src="https://www.thedailyjim.be/assets/profilepic/jimmycabuy.webp"
        alt="jimmycabuy"
        class="object-cover h-auto rounded-3xl aspect-square object-top"
      />
    </div>
    <div class="w-full flex gap-5 flex-col lg:w-1/2">
      <h2 class="text-2xl lg:text-4xl">
        I'm a front-end developer & photographer working in sunny Brussels,
        Belgium.
      </h2>
      <p class="leading-8 text-justify sm:text-left">
        I graduated with a degree in e-business from EPHEC and spent over 2
        years at a digital marketing agency as a content creator, social ads
        expert, and social media manager. I then traveled the world for 6
        months, capturing unique moments and landscapes as a photographer. I
        expanded my technical skills with an intensive JavaScript Bootcamp and
        became a front-end developer at Decathlon Belgium, combining my diverse
        experiences to create exceptional web experiences.
      </p>
      <p>
        My journey has shaped me into a curious and creative professional,
        always seeking new challenges and pushing my skills to the limit.
      </p>
    </div>
  </div>
</main>

<style>
  h1 {
    animation-duration: 1s;
    animation-fill-mode: both;
  }

  h1 {
    animation-name: fadeInBottom;
  }
  @keyframes fadeInBottom {
    from {
      opacity: 0;
      transform: translateY(-100%);
    }
    to {
      opacity: 1;
    }
  }
  h2,
  p,
  img {
    animation: fadein 2.5s;
    -moz-animation: fadein 2.5s;
    -webkit-animation: fadein 2.5s;
    -o-animation: fadein 2.5s;
  }
  @keyframes fadein {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  h1 {
    color: transparent;
    -webkit-text-stroke: 2px #fff;
    font-weight: 700;
  }
</style>
