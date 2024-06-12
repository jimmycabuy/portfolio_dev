<script>
  import form from "../data/form.json";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  export let isLoading, isMessageSent;

  onMount(() => {
    gsap.from(".get_in_touch", {
      y: -100,
      duration: 1,
      delay: 0.5,
      opacity: 0,
    });
    gsap.from(".one_element_form", {
      y: 50,
      duration: 1,
      delay: 1.5,
      opacity: 0,
      stagger: 0.3,
    });
    gsap.from(".send_button", {
      duration: 3,
      delay: 3.7,
      opacity: 0,
    });

    const formElement = document.querySelector("#form_container");
    formElement.addEventListener("submit", (event) => {
      event.preventDefault();
      const data = new URLSearchParams(new FormData(formElement));
      fetch("https://getform.io/f/e0fcd5ea-3300-4659-8085-c6108ccbef1a", {
        method: "POST",
        body: data,
      });
      setTimeout(() => {
        isLoading = false;
      }, 1500);
      isMessageSent = true;
    });
  });
</script>

<main class="container_contact">
  <h1 class="get_in_touch text-3xl md:text-5xl pb-3">Get in touch.</h1>
  <form
    action="https://getform.io/f/e0fcd5ea-3300-4659-8085-c6108ccbef1a"
    method="POST"
    id="form_container"
  >
    {#each form as { tag, label, type, name, inputmode, required, autocomplete }}
      <div class="one_element_form">
        <label for={name}>{label}</label>
        {#if tag === "input"}
          <input
            {type}
            {name}
            id={name}
            {inputmode}
            {required}
            {autocomplete}
          />
        {:else if tag === "textarea"}
          <textarea {name} id={name} {required} {autocomplete} />
        {/if}
      </div>
    {/each}
    <input
      type="hidden"
      name="_gotcha"
      style="display:none !important"
      autocomplete="off"
    />
    <div class="send_button flex justify-center">
      <button type="submit" class="enlarged">Send</button>
    </div>
  </form>
</main>

<style>
  .container_contact {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 1rem;
  }

  #form_container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    width: 60%;
  }

  .one_element_form {
    display: flex;
    flex-direction: column;
  }

  button {
    border-radius: 10px;
    padding: 0.5rem;
  }

  input,
  textarea,
  button {
    font-family: "bd-supper", sans-serif;
    font-style: normal;
  }

  label {
    font-size: 0.9rem;
  }

  input,
  textarea {
    border: none;
    font-size: 0.9rem;
    background: none;
    border-radius: 0;
    -webkit-appearance: none;
    appearance: none;
  }

  input {
    height: 2rem;
    border-bottom: 1px solid #fff;
  }

  textarea {
    resize: none;
    border-bottom: 1px solid #fff;
    height: 8rem;
    padding-top: 0.5rem;
  }

  button {
    background: none;
    border: 1px solid #fff;
    width: 15rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
    color: #fff;
    font-size: 0.9rem;
    transition: 0.3s;
  }

  button:hover {
    color: #000;
    background-color: #fff;
  }

  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  h1 {
    font-weight: 700;
    color: transparent;
    -webkit-text-stroke: 1px #fff;
  }

  @media (max-width: 767px) {
    #form_container {
      width: 85%;
    }
  }
</style>
