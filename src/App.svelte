<script>
  import Message from "./Message.svelte";
  export let name;
  let message = "";
  let messages = [];

  function saveMessage() {
    const newMessage = {
      id: Date.now(),
      text: message,
      author: "Sam"
    };
    messages = [newMessage, ...messages];
    message = "";
  }
</script>

<style>
  h1 {
    color: rgb(89, 144, 216);
  }
</style>

<Message />

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div>By {message.author}</div>
    <div> {message.text} </div>
    <hr />
  {/each}
</div>
