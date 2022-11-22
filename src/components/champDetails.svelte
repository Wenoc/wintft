<script>
  export let hidden;
  export let AllChampions;
  export let actualNamename;
  export let name;
  export let opt;

  let items = [];

  if (AllChampions) {
    items = AllChampions.BestItems;
    for (let i = 0; i < items.length; i++) {
      items[i] = items[i].replaceAll("'", "");
      items[i] = items[i].replaceAll(" ", "");
    }
  }

  function traitChange(t) {
    t = t.replaceAll(" ", "");
    if (t == "Underground") {
      return "theunderground";
    } else if (t == "Mecha:PRIME") {
      return "mechaprime";
    } else {
      t = t.toLowerCase();
      return t;
    }
  }
</script>

<div class="ChampDetailContainer" class:hidden={hidden || opt}>
  <div class="up">
    <div class="left">
      <div class="lup">
        <div style="border: 2px solid black; height:65px; border-radius:3px">
          <img src="./ChampIcons/tft8_{name}.webp" alt="a" height="65" />
        </div>
      </div>
      <div class="ldown">
        <p>{actualNamename}</p>
      </div>
    </div>
    <div class="right">
      {#if AllChampions}
        {#each AllChampions.Traits as trait}
          <div class="trait">
            <img
              src="./Traits/{traitChange(trait.Name)}.webp"
              alt="s"
              height="32"
              width="32"
            />
            <p>{trait.Name}</p>
          </div>
        {/each}
      {/if}
    </div>
  </div>
  <div class="down">
    <div class="dleft">
      <p style="margin-right: 8px;">Best items:</p>
      {#each items as item}
        <img src="./items/{item}.webp" alt="b" height="32" width="32" />
      {/each}
    </div>
    <div class="dright">
      <img
        src="./random/coins.svg"
        alt="coin"
        decoding="async"
        height="22"
        width="22"
        loading="lazy"
      />
      {#if AllChampions}
        <p>{AllChampions.Cost}</p>
      {/if}
    </div>
  </div>
</div>

<style>
  .hidden {
    display: none;
  }

  .ChampDetailContainer {
    position: absolute;
    z-index: 3;
    bottom: 80px;
    right: -140px;
    width: 340px;
    height: 200px;
    background-color: #22242f;
    border: 1px solid #5e5d5d;
  }
  .up {
    border-bottom: 1px solid #5e5d5d;
    height: 150px;
    display: flex;
  }

  .dleft {
    display: flex;
    align-items: center;
    gap: 4px;
    width: 100%;
  }

  .dright {
    width: 60px;
    align-items: center;
    justify-content: center;
    display: flex;
    gap: 4px;
  }

  .down {
    height: 50px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding-left: 10px;
    gap: 4px;
  }

  .left {
    width: 120px;
    height: 100%;
    border-right: 1px solid #5e5d5d;
    display: flex;
    flex-direction: column;
  }

  .right {
    width: 220px;
    height: 100%;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 6px;
    box-sizing: border-box;
  }

  .lup {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }
  .ldown {
    height: 60%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .trait {
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .trait img {
    height: 24px;
    width: 24px;
  }

  p {
    color: white;
    margin: 0;
    font-size: 16px;
  }

  @media (max-width: 800px) {
    .ChampDetailContainer {
      display: none;
    }
  }
</style>
