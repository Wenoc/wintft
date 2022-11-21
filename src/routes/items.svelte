<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("/itemData.json");
    const standardItems = await res.json();

    const res2 = await this.fetch("/gadgeteenItems.json");
    const gadgeteenItems = await res2.json();

    const res3 = await this.fetch("/emblems.json");
    const emblems = await res3.json();
    let combine = [];

    combine[0] = standardItems;
    combine[1] = gadgeteenItems;
    combine[2] = emblems;
    // combine[3] = itemData;

    return { combine };
  }
</script>

<script>
  export let combine;
  let standardItems = combine[0];
  let gadgeteenItems = combine[1];
  let emblems = combine[2];
  import Header from "../components/Header.svelte";
  import PageLayout from "../components/PageLayout.svelte";

  let sC1 = "chain";
  let sC2 = "belt";
  let sIconName = "Gargoyle's Stoneplate";
  let sIconSrc = "GargoylesStoneplate";
  let sIconDescription =
    "Grants 16 Armor and 16 Magic Resist for each enemy targeting the holder.";
  function showDetails(nm, src, dsc, c1, c2) {
    sIconName = nm;
    sIconSrc = src;
    sIconDescription = dsc;
    sC1 = c1;
    sC2 = c2;
  }

  let actualItems = standardItems;

  function standard() {
    actualItems = standardItems;
  }

  function gadgeteen() {
    actualItems = gadgeteenItems;
  }

  function emblem() {
    actualItems = emblems;
  }
</script>

<svelte:head>
  <title>TFT Set 8 Item Recipes and Descriptions - WinTFT</title>
  <meta
    name="description"
    content="TFT Item builder and guide. Standard Items, Gadgeteen items, Radiant items, Emblems"
  />
</svelte:head>

<PageLayout>
  <div slot="middle">
    <Header headerText="Item Builder" />
    <div class="itemContainer">
      <div class="up">
        <div class="selectItem" on:click={standard}>
          <p>Standard</p>
        </div>
        <div class="selectItem" on:click={gadgeteen}>
          <p>Gadgeteen</p>
        </div>
        <div class="selectItem" on:click={emblem}>
          <p>Emblems</p>
        </div>
      </div>
      <div class="down">
        <div class="items">
          {#each actualItems as item}
            <div class="item">
              <img
                on:click={showDetails(
                  item.name,
                  item.icon,
                  item.description,
                  item.component1,
                  item.component2
                )}
                src="items/{item.icon}.webp"
                alt={item}
                height="40"
                width="40"
              />
            </div>
          {/each}
        </div>
        <div class="description">
          <div class="iconName">
            <img
              src="items/{sIconSrc}.webp"
              alt={sIconSrc}
              height="40"
              width="40"
            />
            <p>{sIconName}</p>
          </div>
          {#if sC1 != "-"}
            <div class="rec">
              <div>
                <img
                  src="items/{sC1}.webp"
                  alt="{sC1}.webp"
                  height="30"
                  width="30"
                />
              </div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                height="24"
                width="24"
                ><g data-name="Layer 2"
                  ><g data-name="plus"
                    ><rect
                      width="24"
                      height="24"
                      opacity="0"
                      transform="rotate(180 12 12)"
                    /><path
                      fill="white"
                      d="M19 11h-6V5a1 1 0 0 0-2 0v6H5a1 1 0 0 0 0 2h6v6a1 1 0 0 0 2 0v-6h6a1 1 0 0 0 0-2z"
                    /></g
                  ></g
                ></svg
              >
              <div>
                <img
                  src="items/{sC2}.webp"
                  alt="{sC2}.webp"
                  height="30"
                  width="30"
                />
              </div>
            </div>
          {/if}
          <div class="desc">
            <p>{sIconDescription}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</PageLayout>

<style>
  .rec {
    display: flex;
    gap: 6px;
    align-items: center;
    margin-top: 10px;
  }
  .desc {
    white-space: pre-line;
    margin-top: 12px;
    font-weight: 400;
  }

  .desc p {
    white-space: pre-line;
    font-size: 18px;
  }
  .iconName {
    display: flex;
    gap: 12px;
    align-items: center;
  }
  .item {
    cursor: pointer;
    height: 40px;
  }
  .items {
    display: flex;
    flex-wrap: wrap;
    margin-top: 20px;
    gap: 4px;
    line-height: 0;
  }
  .description {
    padding: 10px;
    margin-top: 20px;
    height: 310px;
    border: 1px solid #5e5d5d;
  }
  .up {
    display: flex;
    justify-content: flex-start;
    gap: 14px;
    flex-wrap: wrap;
  }

  .down {
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  p {
    color: white;
    font-size: 20px;
    margin: 0;
  }
  .selectItem {
    background-color: #13141b;
    padding: 8px 16px;
    border-radius: 2px;
    height: 30px;
    cursor: pointer;
  }
  .itemContainer {
    display: flex;
    flex-direction: column;
    padding: 16px;
    width: 1000px;
    background-color: #22242f;
    border-radius: 3px;
  }
  @media (max-width: 1110px) {
    .itemContainer {
      width: 600px;
    }
  }
  @media (max-width: 720px) {
    .desc p {
      font-size: 16px;
    }
    .itemContainer {
      width: 300px;
    }

    .iconName p {
      margin-top: 2px;
      font-size: 16px;
    }

    .up {
      gap: 6px;
      box-sizing: border-box;
      flex-wrap: nowrap;
      justify-content: center;
    }

    .selectItem {
      padding: 6px 10px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .selectItem p {
      font-size: 16px !important;
    }

    .items {
      line-height: 0;
      height: 50%;
    }

    .item img {
      height: 32px;
      width: 32px;
    }
    .item {
      height: 32px;
      width: 32px;
    }

    .description {
      height: 90%;
    }

    .selectItem p {
      font-size: 20px;
      height: auto;
    }
  }
</style>
