<script>
  import Spinner from '../../components/Spinner.svelte';
  import ContactForm from '../../components/ContactForm.svelte';
  import MessageSent from '../../components/MessageSent.svelte';

  let isMessageSent = false;
  let isLoading = true;

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
  <ContactForm bind:isLoading bind:isMessageSent />
{:else if isLoading}
  <Spinner />
{:else}
  <MessageSent />
{/if}
