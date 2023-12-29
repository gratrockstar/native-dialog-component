<script>
  import { Dialog } from '$lib';
  let dialog;
</script>

<button on:click={() => dialog.showModal()}>Open It!</button>

<Dialog bind:dialog animated="true">
  <h2 slot="header">
		Here's our modal
	</h2>
  <p>Here's a dialog.</p>
  <p>It can have some content if we want!</p>
  <div slot="footer">
    <p>Here's some more content for the footer.</p>
  </div>
</Dialog>
