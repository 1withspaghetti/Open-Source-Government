<script lang="ts">
  import App from '$lib/components/App.svelte'
    import ScrollText from '$lib/components/ScrollText.svelte';
</script>

<div>
  <App />
</div>
<ScrollText />

<style>
  :global(html) {
    background: rgb(13, 19, 32);
    background: linear-gradient(180deg, rgba(13, 19, 32, 1) 0%, rgba(8, 12, 21, 1) 100%);
  }

  :global(body) {
    min-height: 500vh;
    margin: 0;
  }

  div {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
    width: 100vw;
    height: 100vh;
    background: rgb(13, 19, 32);
    background: linear-gradient(180deg, rgba(13, 19, 32, 1) 0%, rgba(8, 12, 21, 1) 100%);
  }
</style>
