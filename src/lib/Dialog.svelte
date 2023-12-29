<script>
  export let dialog;
  export let animated = false;
</script>

<!-- svelte-ignore a11y-click-events-have-key-events a11y-no-noninteractive-element-interactions -->
<dialog 
  bind:this={dialog} 
  on:close
  on:click|self={() => dialog.close()}
  class="dialog"
  class:animated={animated}
>
  <div class="dialog-header">
    <slot name="header" />
  </div>
  <div class="dialog-content">
    <slot/>
  </div>
  <div class="dialog-footer">
    <slot name="footer" />
    <!-- svelte-ignore a11y-autofocus -->
    <button autofocus on:click={() => dialog.close()}>Close</button>
  </div>
</dialog>

<style lang="scss">
  dialog.animated {
    animation: fade-out 150ms ease-out;
  }

  dialog.animated[open] {
    animation: fade-in 250ms ease-out;
  }

  dialog.animated::backdrop {
    animation: backdrop-fade-out 250ms ease-out forwards;
  }

  dialog.animated[open]::backdrop {
    animation: backdrop-fade-in 250ms ease-out forwards;
  }

  @keyframes fade-in {
    0% {
      opacity: 0;
      transform: translateY(-50%);
      display: none;
    }

    100% {
      opacity: 1;
      transform: translateY(0%);
      display: block;
    }
  }

  @keyframes fade-out {
    0% {
      opacity: 1;
      transform: translateY(0%);
      display: block;
    }

    100% {
      opacity: 0;
      transform: translateY(-50%);
      display: none;
    }
  }

  @keyframes backdrop-fade-in {
    0% {
      background-color: rgb(0 0 0 / 0);
    }

    100% {
      background-color: rgb(0 0 0 / 0.45);
    }
  }

  @keyframes backdrop-fade-out {
    0% {
      background-color: rgb(0 0 0 / 0.45);
    }

    100% {
      background-color: rgb(0 0 0 / 0);
    }
  }
</style>