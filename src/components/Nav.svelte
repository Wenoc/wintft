<script>
  export let segment;
  import NavBlogItem from "./NavBlogItem.svelte";
  import { onMount } from "svelte";
  let isHover = false;

  function showStuff() {
    let expandNav = document.querySelector(".expand");
    if (expandNav.clientHeight) {
      expandNav.style.height = 0;
      expandNav.style.borderBottom = 0;
    } else {
      expandNav.style.height = 150 + "px";
      expandNav.style.border = "1px solid #5e5d5d";
      expandNav.style.borderTop = 0;
      expandNav.style.borderRight = 0;
      expandNav.style.borderLeft = 0;
    }
  }
</script>

<nav>
  <div class="navContainer">
    <div style="padding-top: 8px;">
      <a href="."
        ><svg
          width="120"
          height="31"
          viewBox="0 0 139 31"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M37.44 2.44L30.68 31H23.16L20 16C19.9467 15.7067 19.8667 15.2667 19.76 14.68C19.6533 14.0933 19.5333 13.4533 19.4 12.76C19.2933 12.0667 19.1867 11.4133 19.08 10.8C19 10.16 18.9333 9.66666 18.88 9.32C18.8533 9.66666 18.7867 10.16 18.68 10.8C18.5733 11.4133 18.4533 12.0667 18.32 12.76C18.2133 13.4267 18.1067 14.0667 18 14.68C17.8933 15.2667 17.8 15.72 17.72 16.04L14.56 31H7.04L0.28 2.44H6.6L9.76 18.04C9.84 18.4933 9.94667 19.0533 10.08 19.72C10.2133 20.36 10.3467 21.04 10.48 21.76C10.6133 22.4533 10.7333 23.1333 10.84 23.8C10.9467 24.4667 11.0267 25.04 11.08 25.52C11.16 25.0133 11.2533 24.44 11.36 23.8C11.4933 23.1333 11.6133 22.4533 11.72 21.76C11.8533 21.0667 11.9733 20.4267 12.08 19.84C12.2133 19.2267 12.32 18.7333 12.4 18.36L15.88 2.44H21.88L25.28 18.44C25.36 18.7867 25.4533 19.2667 25.56 19.88C25.6933 20.4667 25.8267 21.1067 25.96 21.8C26.0933 22.4933 26.2133 23.1733 26.32 23.84C26.4267 24.48 26.52 25.04 26.6 25.52C26.68 24.8533 26.8 24.0667 26.96 23.16C27.12 22.2267 27.2933 21.2933 27.48 20.36C27.6667 19.4267 27.8267 18.6533 27.96 18.04L31.12 2.44H37.44ZM46.8544 9.16V31H40.4544V9.16H46.8544ZM43.6944 0.599998C44.6277 0.599998 45.4277 0.813332 46.0944 1.24C46.761 1.64 47.0944 2.4 47.0944 3.52C47.0944 4.61333 46.761 5.37333 46.0944 5.8C45.4277 6.22667 44.6277 6.44 43.6944 6.44C42.7344 6.44 41.921 6.22667 41.2544 5.8C40.5877 5.37333 40.2544 4.61333 40.2544 3.52C40.2544 2.4 40.5877 1.64 41.2544 1.24C41.921 0.813332 42.7344 0.599998 43.6944 0.599998ZM64.6103 8.76C66.797 8.76 68.557 9.4 69.8903 10.68C71.2503 11.9333 71.9303 13.96 71.9303 16.76V31H65.5303V18.24C65.5303 16.6667 65.2903 15.4933 64.8103 14.72C64.357 13.92 63.6236 13.52 62.6103 13.52C61.0636 13.52 60.0236 14.1467 59.4903 15.4C58.957 16.6267 58.6903 18.4 58.6903 20.72V31H52.2903V9.16H57.1303L58.0103 11.96H58.2903C58.7436 11.2133 59.277 10.6133 59.8903 10.16C60.5303 9.68 61.2503 9.33333 62.0503 9.12C62.8503 8.88 63.7036 8.76 64.6103 8.76ZM88.7713 31H82.2913V7.48H75.3713V2.44H95.6913V7.48H88.7713V31ZM106.043 31H99.6834V2.44H115.323V7.4H106.043V14.76H114.683V19.72H106.043V31ZM131.232 31H124.752V7.48H117.832V2.44H138.152V7.48H131.232V31Z"
            fill="white"
          />
        </svg></a
      >
    </div>
    <div class="burger" on:click={showStuff}>
      <img src="menu.svg" alt="" />
    </div>
    <div class="linkContainer">
      <a
        rel="external"
        href="team-comps/"
        class:selected={segment === "team-comps"}
      >
        <div class="navItem">Team Comps</div>
      </a>
      <a
        rel="external"
        href="augments/"
        class:selected={segment === "augments"}
      >
        <div class="navItem">Augments</div>
      </a>
      <a
        rel="external"
        href="champions/"
        class:selected={segment === "champions"}
      >
        <div class="navItem">Champions</div>
      </a>
      <a
        rel="external"
        href="guides"
        class="guides navItem"
        class:selected={segment === "guides"}
        style="display: flex; justify-content: center; align-items: center;"
      >
        <div>Guides</div>
      </a>
    </div>
  </div>
</nav>
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
  <a rel="external" href="champions/" class:selected={segment === "champions"}>
    <div class="navItem">Champions</div>
  </a>
  <a rel="external" href="guides/" class:selected={segment === "guides"}>
    <div class="navItem">Guides</div>
  </a>
</div>

<style>
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
  .brand {
    height: 50px;
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
  }
</style>
