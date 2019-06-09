<script>
  import Message from "./Message.svelte";
  export let name;
  let message = "";
  let messages = [];
</script>

<style>

</style>

<Message author="Bob" />

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div>By {message.author}</div>
    <div> {message.text} </div>
    <hr />
  {/each}
</div>
