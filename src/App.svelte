<script>
  import Message from "./Message.svelte";
  export let name;
  let message = "";
  let messages = [];

  function addMessage(event) {
		console.log(event);
		messages = [event.detail, ...messages];
  }
</script>

<style>

</style>

<Message author="Bob" on:message={addMessage} />

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div>By {message.author}</div>
    <div> {message.text} </div>
    <hr />
  {/each}
</div>
