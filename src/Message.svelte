<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let author = "";
  let message = "";
  $: nbCaracters = message.length;
  $: disabled = message.length > 12 ? true : false;

  function saveMessage() {
    const newMessage = {
      id: Date.now(),
      text: message,
      author: author,
      date: new Date()
    };
    console.log("newMessage", newMessage);
    dispatch("message", newMessage);
    message = "";
    author = "";
  }
</script>

<style>
  .text {
    width: 382px;
  }
</style>

<input class="text" type="text" bind:value={author} />
<br />
<textarea cols="50" rows="5" bind:value={message} />
<br />
<button on:click={saveMessage} disabled={disabled}>send</button>
<span>{nbCaracters}</span>
