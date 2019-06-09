<script>
  export let name;
  let message = "";
  let messages = [];

  function updateMessage(event) {
    message = event.target.value;
  }

  function saveMessage() {
    const newMessage = {
      id: Date.now(),
      text: message,
      author: "Sam"
    };
    messages = [newMessage, ...messages];
  }
</script>

<style>
  h1 {
    color: rgb(89, 144, 216);
  }
</style>

<h1>Hello {name}!</h1>
<textarea cols="50" rows="5" on:input={updateMessage} />
<br />
<button on:click={saveMessage}>send</button>
<div>
  <h3>Preview</h3>
   {message}
</div>

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div>By {message.author}</div>
    <div> {message.text} </div>
    <hr />
  {/each}
</div>
