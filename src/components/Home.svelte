<script>
  import Skills from "./Skills.svelte";
  const banner = "/assets/banner.webp";
  const pdf = "/document/jimmy_cabuy_resume.pdf";
</script>

<main class="flex-1 bg-zinc-800 flex justify-center items-center">
  <div class="container_home flex justify-between py-6 px-12 items-center">
    <div class="profile-container max-w-[50%]">
      <div class="flex flex-col gap-6">
        <div>
          <h3 class="inline-block">Front-end developer & photographer</h3>
        </div>
        <h1 class="text-7xl">Jimmy Cabuy</h1>
        <p>
          <!-- Hey! I'm Jimmy, a versatile full-stack web/mobile developer, web
          designer, and photographer. With a degree in e-business, I gained over
          2 years of experience in digital marketing, specializing in content
          creation, social ads, and social media management. I then embarked on
          a 6-month adventure capturing the essence of diverse cultures and
          landscapes through my camera lens. Passionate about web development, I
          completed an intensive JavaScript Bootcamp, solidifying my technical
          foundations. Currently, I'm thrilled to be a front-end developer at
          Decathlon, creating exceptional web experiences. My journey from
          digital marketing to world exploration and web development has shaped
          me into a curious and creative professional, constantly seeking new
          challenges. -->
          Hi! I'm Jimmy, a versatile full-stack developer, designer, and photographer
          with a degree in e-business. I have 2+ years of digital marketing experience,
          specializing in content creation and social media management. After a 6-month
          photography adventure, I completed a JavaScript Bootcamp and now work as
          a front-end developer at Decathlon. I'm a curious and creative professional
          always seeking new challenges.
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
    <div class="image-container max-w-[50%]">
      <!-- svelte-ignore a11y-img-redundant-alt -->
      <img src={banner} alt="Jimmy_Cabuy_banner" class="image_banner" />
    </div>
  </div>
</main>

<style>
  main {
    height: 80vh;
    max-height: 80vh;
    overflow: hidden;
  }
  h3 {
    /* background-color: #fff; */
    border: 2px solid #fff;
    color: #fff;
    padding: 0.25rem 1rem 0.25rem 1rem;
    border-radius: 20px;
    text-align: center;
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

  .image-container {
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
  .image_banner {
    max-width: 75%;
    max-height: 75%;
  }

  @media (max-width: 767px) {
    h1 {
      font-size: xxx-large;
    }
    h3 {
      font-size: smaller;
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
      max-width: 90%;
    }
    .image-container {
      max-width: 90%;
      justify-content: center;
      margin-top: 2rem;
    }

    p {
      text-align: justify;
    }
  }
</style>
