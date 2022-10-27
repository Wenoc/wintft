<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("/augmentData.json");
    const augmentData = await res.json();

    return { augmentData };
  }
</script>

<script>
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
</script>

<svelte:head>
  <title>TFT Augment Tier List for Patch 12.20b, Set 7.5 - WinTFT</title>
  <meta
    name="description"
    content="If you want to know what the best augments are at the moment or you don't know what an augment does, WinTFT helps you with that - Patch 12.20b, Set 7.5"
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
                placeholder="Seach Augment"
                bind:value={kereses}
              />
            </div>
          </div>
          <div class="updateContainer">
            <p style="padding: 0; margin: 0;">Last updated: 19, Aug 2022</p>
          </div>
        </div>
        <div>
          <div class="augmentHead" style="text-align:center">
            <div style="width: 30%;">
              <p>Augment</p>
            </div>
            <div style="width: 10%;">
              <p>Tier</p>
            </div>
            <div style="width: 60%;">
              <p>Description</p>
            </div>
          </div>
          {#each seachedAugments as augment}
            <Augment
              name={augment.name}
              Description={augment.description}
              tier={augment.tier}
              src={augment.src}
              isSecond={isSecond()}
              color={findColor(augment.tier)}
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
  .searchContainer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .augmentHead {
    font-weight: 500;
    margin-top: 20px;
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

  .updateContainer {
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    color: white;
    padding: 6px 10px;
    margin: 0;
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
    margin-bottom: 70px;
  }

  @media (max-width: 1100px) {
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
    .updateContainer {
      display: none;
    }

    .augmentHead {
      justify-content: space-between;
    }
    .searchContainer {
      justify-content: center;
    }
  }
</style>
