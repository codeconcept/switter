<script>
	export let name;
	let message = "inital message value";

	function updateMessage(event) {
		message = event.target.value;
	}
</script>

<style>
	h1 {
		color: rgb(89, 144, 216);
	}
</style>

<h1>Hello {name}!</h1>
<textarea cols="50" rows="5" value={message} on:input={updateMessage}></textarea>
<div>
  <h3>Preview</h3>
  {message}
</div>
