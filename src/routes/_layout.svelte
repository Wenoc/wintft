<script>
  import Footer from "../components/Footer.svelte";
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<div class="fixed-top">
  <Nav {segment} />
</div>

<main>
  <slot />
</main>

<div class="footer">
  <Footer />
</div>

<style>
  .fixed-top {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    z-index: 10;
  }
  .footer {
    width: 100%;
    margin-top: auto;
    bottom: 0;
    position: static;
  }

  main {
    min-height: 882px;
  }
</style>
