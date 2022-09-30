<script>
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<div class="fixed-top">
  <Nav {segment} />
</div>

<main>
  <slot />
</main>

<style>
  .fixed-top {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    z-index: 10;
  }
</style>
