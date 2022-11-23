<script context="module">
  // console.log('module script');
  export async function preload(page, session) {
    const res = await this.fetch("/ChampData.json");
    const AllChampions = await res.json();

    const res2 = await this.fetch("./ItemsData/itemData.json");
    const ItemData = await res2.json();

    let combine = [];
    combine[0] = AllChampions;
    combine[1] = ItemData;

    return { combine };
  }
</script>

<script>
  import ChampionsChamp from "../../components/ChampionsChamp.svelte";
  import Header from "../../components/Header.svelte";
  import { flip } from "svelte/animate";
  import PageLayout from "../../components/PageLayout.svelte";
  import Champ from "../../components/Champ.svelte";

  export let combine;
  let AllChampions = combine[0];
  let itemData = combine[1];

  let kereses = "";

  let searchedChampions = AllChampions;

  function getChampTraits(traits) {
    let newTraits = [];
    for (let i = 0; i < traits.length; i++) {
      let newItem;

      newItem = traits[i].Name.replaceAll("'", "");
      newTraits[i] = newItem;
    }

    return newTraits;
  }

  function champKereses() {
    return AllChampions.filter(
      (line) =>
        line.Name.toLowerCase().includes(kereses.toLocaleLowerCase()) == true
    );
  }

  $: {
    kereses;
    searchedChampions = champKereses();
  }

  function champItems(items) {
    let newItems = [];

    for (let i = 0; i < 3; i++) {
      let newItem;
      newItem = items[i].replaceAll("'", "");
      newItem = newItem.replaceAll(" ", "");
      newItems[i] = newItem;
    }
    return newItems;
  }

  function bg(champ) {
    return champ.replaceAll(" ", "-");
  }
</script>

<svelte:head>
  <title>TFT Champions and Item Builds for Set 8 - WinTFT</title>
  <meta
    name="description"
    content="Discover all champions' traits, costs, and the best items you can build on them here in one place with WinTFT - Set 8"
  />
</svelte:head>

<PageLayout>
  <div slot="middle">
    <Header headerText="Champions" />
    <div class="champPageContainer">
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
      </div>
      <div class="championsContainer">
        <div class="divinContainer">
          {#each searchedChampions as Champ (Champ.Name)}
            <div animate:flip={{ duration: 300 }}>
              <ChampionsChamp
                {itemData}
                name={Champ.Name}
                traits={getChampTraits(Champ.Traits)}
                items={Champ.BestItems}
                cost={Champ.Cost}
                bg={bg(Champ.Name)}
              />
            </div>
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
  .champPageContainer {
    width: 1000px;
  }

  .championsContainer .divinContainer {
    max-width: 1000px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
  }

  .championsContainer {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .searchContainer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-direction: row;
    max-width: 974px;
    margin: 0 auto;
    margin-bottom: 20px;
  }

  .searchBox div input {
    min-width: 225px;
    padding-top: 3px;
    font-size: 16px;
    font-weight: 600;
    padding-left: 8px;
    height: 32px;
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    outline: none;
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

  @media (max-width: 1100px) {
    .searchContainer {
      justify-content: center;
    }
    .champPageContainer {
      width: 680px;
    }
  }

  @media (max-width: 800px) {
    .searchContainer {
      justify-content: center;
    }
    .championsContainer .divinContainer {
      gap: 12px;
    }
  }

  @media (max-width: 700px) {
    .champPageContainer {
      width: 100%;
    }
    .championsContainer .divinContainer {
      gap: 12px;
      flex-direction: column;
    }

    .searchContainer {
      justify-content: center;
    }
  }
</style>
