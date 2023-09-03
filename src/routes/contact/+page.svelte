<script>
  import { onMount } from "svelte";
  import Spinner from "../../components/Spinner.svelte";
  import form from "../../data/form.json";
  let isMessageSent = false;
  let isLoading = true;

  onMount(() => {
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

  $: if (isMessageSent) {
    setTimeout(() => {
      isMessageSent = false;
    }, 7000);
  }
</script>

<svelte:head>
  <title>Jimmy C. | Contact.</title>
</svelte:head>

{#if !isMessageSent}
  <div class="container_contact">
    <h1 class="text-3xl md:text-5xl pb-3">Get in touch.</h1>
    <form
      action="https://getform.io/f/e0fcd5ea-3300-4659-8085-c6108ccbef1a"
      method="POST"
      id="form_container"
    >
      {#each form as item}
        <div class="one_element_form">
          <label for={item.name}>{item.label}</label>
          <input
            type={item.type}
            name={item.name}
            id={item.name}
            required={item.required}
            autocomplete={item.autocomplete}
          />
        </div>
      {/each}
      <div class="one_element_form">
        <label for="message">Message*</label>
        <textarea name="message" id="message" required autocomplete="off" />
      </div>
      <input
        type="hidden"
        name="_gotcha"
        style="display:none !important"
        autocomplete="off"
      />
      <div class="flex justify-center">
        <button type="submit">Send</button>
      </div>
    </form>
  </div>
{:else if isLoading}
  <Spinner />
{:else}
  <div class="flex flex-col items-center gap-4 text-center">
    <p>
      I have received your message. <br />Thank you very much. I will get back
      to you as soon as possible. <br />Have a beautiful day!
    </p>
    <a href="/" class="backhome">Go gack home</a>
  </div>
{/if}

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
  form {
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

  input,
  textarea,
  button,
  .backhome {
    font-family: "bd-supper", sans-serif;
    font-weight: 700;
    font-style: normal;
    padding: 0.5rem;
    border-radius: 10px;
  }

  label {
    font-size: 0.9rem;
  }

  input,
  textarea {
    border: none;
    font-size: 0.9rem;
    padding-left: 0.5rem;
    background: none;
  }

  input {
    height: 2.5rem;
    border: 1px solid #fff;
  }

  textarea {
    resize: none;
    border: 1px solid #fff;
    height: 8rem;
    padding-top: 0.5rem;
  }

  button,
  .backhome {
    background: none;
    border: 1px solid #fff;
    width: 15rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
    color: #fff;
    font-size: 0.9rem;
    transition: 0.3s;
  }

  button:hover,
  .backhome:hover {
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
      width: 95%;
    }
  }
</style>
