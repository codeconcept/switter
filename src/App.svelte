<script>
  import Message from "./Message.svelte";
  export let name;
  let message = "";
	let messages = [];

  function addMessage(event) {
    console.log(event);
    messages = [event.detail, ...messages];
  }

  const options = {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
    hour12: true,
    hour: "numeric",
    minute: "2-digit",
    second: "2-digit"
	};
	// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/DateTimeFormat
  const formatter = new Intl.DateTimeFormat("en-US", options);
</script>

<style>
  .author {
    font-weight: bold;
  }
</style>

<Message on:message={addMessage} />

<div>
  <h2>Messages</h2>
  {#each messages as message}
    <div class="author">
      By {message.author} on {formatter.format(message.date)}
    </div>
    <div> {message.text} </div>
    <hr />
  {/each}
</div>
