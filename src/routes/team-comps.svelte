<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("/data.json");
    const AllChampions = await res.json();

    const res2 = await this.fetch("/compData.json");
    const compData = await res2.json();
    let combine = [];

    const res3 = await this.fetch("./AugmentsData/goldAugments.json");
    const augmentData = await res3.json();

    const res4 = await this.fetch("/itemData.json");
    const itemData = await res4.json();

    combine[0] = AllChampions;
    combine[1] = compData;
    combine[2] = augmentData;
    combine[3] = itemData;

    return { combine };
  }
</script>

<script>
  import Header from "../components/Header.svelte";
  import Comp from "../components/Comp.svelte";
  import PageLayout from "../components/PageLayout.svelte";

  export let combine;
  let AllChampions = combine[0];
  let compData = combine[1];
  let augmentData = combine[2];
  let itemData = combine[3];

  function reverseComp(comp) {
    let reversed = Object.values(comp);
    reversed = reversed.reverse();
    return reversed;
  }

  function findColor(tTier) {
    if (tTier == "S") return "ff7e83";
    else if (tTier == "A") return "ffbf7f";
    else if (tTier == "B") return "ffde7f";
    else if (tTier == "C") return "feff7f";
    else if (tTier == "D") return "bffe7f";
  }
</script>

<svelte:head>
  <title>TFT Comp Tier List for Set 8 - WinTFT</title>
  <meta
    name="description"
    content="Discover the strongest TFT team comps that the best players have been playing to always be ahead of your opponents with WinTFT - Patch 12.21, Set 7.5"
  />
</svelte:head>

<PageLayout>
  <div slot="middle">
    <Header headerText="Team Comps" />
    <div class="compsContainer">
      <div class="patchInfo" style="margin-bottom: 20px;">
        <div class="infoRight">
          <div class="blockContainer">
            <p style="padding: 0; margin: 0;">Set 8</p>
          </div>
          <div class="blockContainer">
            <p style="padding: 0; margin: 0;">PBE</p>
          </div>
        </div>
      </div>
      {#each compData as comp}
        <div class="singleCompContainer">
          <Comp
            {itemData}
            tiercolor={findColor(comp.tier)}
            {augmentData}
            {AllChampions}
            threeStar={comp.threeStar}
            id={comp.id}
            name={comp.name}
            tier={comp.tier}
            champions={reverseComp(comp.champions)}
            carousel={comp.carousel}
            augments={comp.augments}
            lvl9={comp.lvl9}
            optionsChampionsRight={comp.optionsChampionsRight}
            optionsChampionsLeft={comp.optionsChampionsLeft}
            Gtraits={comp.traits[0].gold}
            Straits={comp.traits[1].silver}
            Btraits={comp.traits[2].bronze}
            difficulty={comp.difficulty}
            type={comp.type}
            carries={comp.carries}
            positions={comp.positions}
            guide={comp.guide}
          />
        </div>
      {/each}
    </div>
  </div>
</PageLayout>

<style>
  .compsContainer {
    width: 980px;
  }
  .patchInfo {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .patchInfo div:nth-child(1) {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }
  .blockContainer {
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    color: white;
    padding: 6px 10px;
    margin: 0;
  }

  .singleCompContainer {
    display: flex;
    justify-content: center;
  }
  @media (max-width: 1100px) {
    .compsContainer {
      width: 600px;
    }
  }
  @media (max-width: 720px) {
    .compsContainer {
      width: 350px;
    }

    .patchInfo div:nth-child(1) {
      justify-content: space-between;
    }

    .infoRight {
      width: 100%;
      display: flex;
      padding: 0 3px;
    }
  }
</style>
