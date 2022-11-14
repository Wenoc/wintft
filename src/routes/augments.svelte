<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("/augmentData.json");
    const augmentData = await res.json();

    return { augmentData };
  }
</script>

<script>
  import { onMount } from "svelte";
  import Header from "../components/Header.svelte";
  import Augment from "../components/Augment.svelte";
  import PageLayout from "../components/PageLayout.svelte";
  export let augmentData;

  let i = 1;
  function isSecond() {
    let isIt = false;
    if (i % 2 == 0) {
      isIt = true;
    }
    i += 1;
    return isIt;
  }
  var ordering = {};
  const sortOrder = ["S", "A", "B", "C", "D"];

  for (i = 0; i < sortOrder.length; i++) {
    ordering[sortOrder[i]] = i;
  }

  augmentData.sort(function (a, b) {
    return ordering[a.tier] - ordering[b.tier] || a.tier.localeCompare(b.tier);
  });

  var kereses = "";
  let seachedAugments = augmentData;

  function augmentkereses() {
    return augmentData.filter(
      (line) =>
        line.name.toLowerCase().includes(kereses.toLocaleLowerCase()) == true
    );
  }

  $: {
    kereses;
    seachedAugments = augmentkereses();
  }

  function findColor(tTier) {
    if (tTier == "S") return "ff7e83";
    else if (tTier == "A") return "ffbf7f";
    else if (tTier == "B") return "ffde7f";
    else if (tTier == "C") return "feff7f";
    else if (tTier == "D") return "bffe7f";
  }

  function carryClicked() {
    document.querySelector(".carry").style.background = "#22242f";
    document.querySelector(".support").style.background = "#2d2f3a";
    document.querySelector(".silver").style.background = "#2d2f3a";
    document.querySelector(".gold").style.background = "#2d2f3a";
    document.querySelector(".prismatic").style.background = "#2d2f3a";
  }

  function supportClicked() {
    document.querySelector(".support").style.background = "#22242f";
    document.querySelector(".carry").style.background = "#2d2f3a";
    document.querySelector(".silver").style.background = "#2d2f3a";
    document.querySelector(".gold").style.background = "#2d2f3a";
    document.querySelector(".prismatic").style.background = "#2d2f3a";
  }

  function silverClicked() {
    document.querySelector(".silver").style.background = "#22242f";
    document.querySelector(".gold").style.background = "#2d2f3a";
    document.querySelector(".prismatic").style.background = "#2d2f3a";
    document.querySelector(".carry").style.background = "#2d2f3a";
    document.querySelector(".support").style.background = "#2d2f3a";
  }

  function goldClicked() {
    document.querySelector(".gold").style.background = "#22242f";
    document.querySelector(".silver").style.background = "#2d2f3a";
    document.querySelector(".prismatic").style.background = "#2d2f3a";
    document.querySelector(".carry").style.background = "#2d2f3a";
    document.querySelector(".support").style.background = "#2d2f3a";
  }

  function prismaticClicked() {
    document.querySelector(".prismatic").style.background = "#22242f";
    document.querySelector(".gold").style.background = "#2d2f3a";
    document.querySelector(".silver").style.background = "#2d2f3a";
    document.querySelector(".carry").style.background = "#2d2f3a";
    document.querySelector(".support").style.background = "#2d2f3a";
  }
</script>

<svelte:head>
  <title>TFT Augment Tier List for Patch 12.21, Set 7.5 - WinTFT</title>
  <meta
    name="description"
    content="In TFT, there are a lot of augments. WinTFT helps you to choose by giving each augments a ranking. It also displays information about them."
  />
</svelte:head>

<PageLayout>
  <div slot="middle">
    <Header headerText="Augments" />
    <div style="display: flex; justify-content:center;">
      <div class="augmentContainer">
        <div class="searchContainer">
          <div class="searchBox">
            <div class="input-icons">
              <svg
                class="icon"
                xmlns="http://www.w3.org/2000/svg"
                fill="#757575"
                height="25"
                width="25"
                viewBox="0 0 24 24"
              >
                <g data-name="Layer 2">
                  <path
                    d="m20.71 19.29-3.4-3.39A7.92 7.92 0 0 0 19 11a8 8 0 1 0-8 8 7.92 7.92 0 0 0 4.9-1.69l3.39 3.4a1 1 0 0 0 1.42 0 1 1 0 0 0 0-1.42zM5 11a6 6 0 1 1 6 6 6 6 0 0 1-6-6z"
                    data-name="search"
                  />
                </g>
              </svg>
              <input
                type="text"
                class="input-field"
                placeholder="Search"
                bind:value={kereses}
              />
            </div>
          </div>
          <div class="rightContainer">
            <div class="heroAugments">
              <div class="carry" on:click={carryClicked}>
                <p>Carry</p>
              </div>
              <div class="support" on:click={supportClicked}>
                <p>Support</p>
              </div>
            </div>
            <div class="generalAugments">
              <div class="silver" on:click={silverClicked}>
                <p>Silver</p>
              </div>
              <div class="gold" on:click={goldClicked}>
                <p>Gold</p>
              </div>
              <div class="prismatic" on:click={prismaticClicked}>
                <p>Prismatic</p>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="augmentHead" style="text-align:center">
            <div style="width: 30%;">
              <p>Augment</p>
            </div>
            <div style="width: 70%;">
              <p>Description</p>
            </div>
          </div>
          {#each seachedAugments as augment}
            <Augment
              name={augment.name}
              Description={augment.description}
              src={augment.src}
              isSecond={isSecond()}
            />
          {/each}
        </div>
      </div>
    </div>
  </div>
  <!-- <div slot="left" class="leftAD">
    <img src="ad.png" alt="chi" />
  </div>
  <div slot="right" class="leftAD">
    <img src="ad.png" alt="chi" />
  </div> -->
</PageLayout>

<style>
  .rightContainer {
    display: flex;
    gap: 10px;
  }

  .heroAugments {
    display: flex;
    align-items: center;
  }

  .heroAugments div {
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    height: 38px;
    padding: 0px 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  .heroAugments div:nth-child(1) {
    border-right: 0;
  }

  .generalAugments {
    display: flex;
    align-items: center;
  }

  .generalAugments div {
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    height: 38px;
    padding: 0px 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  .generalAugments div:nth-child(1) {
    border-right: 0;
  }

  .generalAugments div:nth-child(2) {
    border-right: 0;
  }

  .heroAugments p {
    font-weight: 400;
  }

  .searchContainer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .augmentHead {
    font-weight: 500;
    margin-top: 10px;
    font-size: 18px;
    display: flex;
    background-color: #22242f;
    color: white;
    height: 38px;
    justify-content: center;
    align-items: center;
    border: 1px solid #5e5d5d;
  }

  p {
    margin: 0;
    color: white;
  }
  .searchBox div input {
    outline: none;
    min-width: 225px;
    padding-top: 3px;
    font-size: 16px;
    font-weight: 600;
    padding-left: 8px;
    height: 32px;
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
  }

  .input-icons svg {
    position: absolute;
    height: 30px;
    padding: 0;
  }

  .input-icons {
    width: 100%;
    position: relative;
  }

  .icon {
    padding: 10px;
    left: 202px;
    top: 5px;
  }

  .input-field {
    color: white;
    font-weight: 400;
  }

  .augmentContainer {
    width: 980px;
  }

  @media (max-width: 1100px) {
    .searchContainer {
      flex-direction: column-reverse;
      justify-content: start;
      gap: 10px;
      align-items: flex-start;
    }
    .augmentContainer {
      width: 600px;
    }
    .augmentHead {
      justify-content: space-between;
    }

    .augmentHead div:nth-child(3) {
      display: none;
    }
    .augmentHead div:nth-child(1) {
      width: 80%;
      text-align: left;
      padding-left: 30px;
    }
    .augmentHead div:nth-child(2) {
      width: 20%;
      padding-right: 30px;
    }
  }

  @media (max-width: 700px) {
    .rightContainer {
      flex-direction: column;
    }
    .augmentHead div:nth-child(3) {
      display: none;
    }
    .augmentHead div:nth-child(1) {
      width: 80%;
      text-align: left;
      padding-left: 20px;
    }
    .augmentHead div:nth-child(2) {
      width: 20%;
      padding-right: 20px;
    }
    .augmentHead {
      justify-content: space-around;
    }
    .augmentContainer {
      width: 350px;
      max-width: 350px;
    }

    .augmentHead {
      justify-content: space-between;
    }
    .searchContainer {
      justify-content: center;
    }
  }
</style>
