# Native Dialog Component

A simple native dialog component for Svelte.  Can be (lightly) animated by passing `animated="true"` into the component.

## Usage:

    <script>
	    import { Dialog } from  '@gratrockstar/native-dialog-component';    
	    let  dialog;    
    </script>   
    
    <button on:click={() => dialog.showModal()}>Open the Modal</button>
    <Dialog bind:dialog animated="true">    
	    <h2 slot="header">    
		    Modal title
	    </h2>    
	    <p>Here's a modal dialog.</p>    
	    <p>It can have whatever content we want!</p>    
	    <div slot="footer">    
		    <p>We can put some extra content into the footer.</p>    
	    </div>    
    </Dialog>