<script context="module">
</script>

<script>
  export let segment;
  import { onMount } from "svelte";
</script>

<nav>
  <div class="navContainer">
    <div style="padding-top: 8px;">
      <a rel="external" sapper:prefetch href="/">
        <img src="navbrand.png" alt="" height="48" />
      </a>
    </div>
    <div class="burger" id="burger" style="position: relative;">
      <img src="menu.svg" alt="" />
    </div>
    <div class="linkContainer">
      <a
        sapper:prefetch
        rel="external"
        href="team-comps/"
        class:selected={segment === "team-comps"}
      >
        <div class="navItem">Team Comps</div>
      </a>
      <a
        sapper:prefetch
        rel="external"
        href="augments/"
        class:selected={segment === "augments"}
      >
        <div class="navItem">Augments</div>
      </a>
      <a
        sapper:prefetch
        rel="external"
        href="champions/"
        class:selected={segment === "champions"}
      >
        <div class="navItem">Champions</div>
      </a>
      <a
        sapper:prefetch
        rel="external"
        href="guides/"
        class="guides navItem"
        class:selected={segment === "guides"}
        style="display: flex; justify-content: center; align-items: center;"
      >
        <div>Guides</div>
      </a>
    </div>
  </div>
</nav>

<input type="checkbox" id="demo" />
<label for="demo">
  <div class="expand" id="grow">
    <a
      rel="external"
      href="team-comps/"
      class:selected={segment === "team-comps"}
    >
      <div class="navItem">Team Comps</div>
    </a>
    <a rel="external" href="augments/" class:selected={segment === "augments"}>
      <div class="navItem">Augments</div>
    </a>
    <a
      rel="external"
      href="champions/"
      class:selected={segment === "champions"}
    >
      <div class="navItem">Champions</div>
    </a>
    <a rel="external" href="guides/" class:selected={segment === "guides"}>
      <div class="navItem">Guides</div>
    </a>
  </div>
</label>

<style>
  #demo {
    display: block;
    width: 40px;
    height: 42px;
    position: absolute;
    top: 10px;
    right: 70px;
    opacity: 0;
    cursor: pointer;
  }

  #grow {
    -moz-transition: height 0.4s;
    -ms-transition: height 0.4s;
    -o-transition: height 0.4s;
    -webkit-transition: height 0.4s;
    transition: height 0.4s;
    height: 0;
    overflow: hidden;
  }
  nav {
    background-color: #22242f;
    height: 65px;
    display: flex;
    justify-content: center;
  }
  .linkContainer {
    display: flex;
    align-items: center;
    gap: 50px;
  }

  .linkContainer .navItem {
    color: white;
    font-size: 21px;
    cursor: pointer;
    border-bottom: 2px solid #22242f;
  }

  .linkContainer .navItem:hover {
    color: #fdbe83;
    transition: color 100ms linear;
  }

  .selected {
    border-bottom: 3px solid #fa9c43 !important;
    transform: scale(0.98);
    transition: border-width 0.1s;
  }

  .selected div {
    color: #fa9c43 !important;
  }

  a {
    text-decoration: none;
    height: 100%;
  }

  .burger {
    display: none;
    margin: 0;
    padding: 0;
    width: 40px;
    height: 40px;
    cursor: pointer;
  }

  .burger img {
    width: 100%;
  }

  .navContainer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    min-width: 1000px;
  }

  .guides {
    color: white;
    font-size: 21px;
    cursor: pointer;
    border-bottom: 2px solid #22242f;
  }

  .guides:hover {
    color: #fdbe83;
    transition: color 100ms linear;
  }

  .expand a {
    color: white;
    margin-bottom: 0 !important;
    height: auto;
  }

  .expand {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    font-size: 20px;
    background-color: #16171f;
  }

  .selected {
    border: 0 !important;
  }

  nav {
    box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.2);
  }

  .navItem {
    padding-top: 4px;
  }

  @media (max-width: 1200px) {
    .navContainer {
      min-width: 83%;
    }
  }

  @media (max-width: 1050px) {
    .linkContainer {
      gap: 30px;
    }
  }

  @media (max-width: 940px) {
    .linkContainer {
      display: none;
    }
    .burger {
      display: block;
    }
    #demo:checked + label .expand {
      height: 150px;
    }
  }

  @media (max-width: 780px) {
    #demo {
      right: 60px;
    }
  }

  @media (max-width: 680px) {
    #demo {
      right: 50px;
    }
  }

  @media (max-width: 550px) {
    #demo {
      right: 40px;
    }
  }

  @media (max-width: 450px) {
    #demo {
      right: 36px;
    }
  }
</style>
