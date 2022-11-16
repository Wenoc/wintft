<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("championdata/Syndra.json");
    const Championdata = await res.json();

    const res2 = await this.fetch("data.json");
    const AllChamp = await res2.json();

    const res3 = await this.fetch("itemData.json");
    const itemData = await res3.json();

    const res4 = await this.fetch("traitData.json");
    const traitData = await res4.json();

    let combine = [];
    combine[0] = Championdata;
    combine[1] = AllChamp;
    combine[2] = itemData;
    combine[3] = traitData;

    return { combine };
  }
</script>

<script>
  import PageLayout from "../../components/PageLayout.svelte";
  import ItemDetails from "../../components/ItemDetails.svelte";
  import Champ from "../../components/Champ.svelte";
  import Trait from "../../components/Trait.svelte";

  export let combine;
  let Championdata = combine[0];
  let AllChamp = combine[1];
  let itemData = combine[2];
  let traitData = combine[3];

  function toBg(x) {
    x = x.toLowerCase();
    x = x.replaceAll("'", "");
    x = x.replaceAll(" ", "");
    return x;
  }

  let borderColor = "#878aa2";

  function determineValue(ch) {
    let cost;
    for (let i = 0; i < AllChamp.length; i++) {
      let changed = AllChamp[i].Name.replaceAll("'", "");
      changed = changed.replaceAll(" ", "");
      changed = changed.toLowerCase();
      if (changed == ch.toLowerCase()) {
        cost = AllChamp[i].Cost;
      }
    }
    return cost;
  }

  function findTrait(nm) {
    for (let i = 0; i < traitData.length; i++) {
      if (traitData[i].Name == nm) {
        return traitData[i];
      }
    }
  }

  let hover1x = false;

  function hover1() {
    setTimeout(() => {
      hover1x = true;
    }, 250);
  }

  function leave1() {
    setTimeout(() => {
      hover1x = false;
    }, 250);
  }

  let hover2x = false;

  function hover2() {
    setTimeout(() => {
      hover2x = true;
    }, 250);
  }

  function leave2() {
    setTimeout(() => {
      hover2x = false;
    }, 250);
  }

  let hover3x = false;

  function hover3() {
    setTimeout(() => {
      hover3x = true;
    }, 250);
  }

  function leave3() {
    setTimeout(() => {
      hover3x = false;
    }, 250);
  }

  function getActual(ch) {
    let actual;
    for (let i = 0; i < AllChamp.length; i++) {
      let changed = AllChamp[i].Name.replaceAll("'", "");
      changed = changed.replaceAll(" ", "");
      changed = changed.toLowerCase();
      if (changed == ch.toLowerCase()) {
        actual = AllChamp[i].Name;
      }
    }
    return actual;
  }
</script>

<PageLayout>
  <div slot="middle">
    <div class="container">
      <div class="arrowContainer">
        <a href="./champions" rel="external">
          <img src="arrow.svg" alt="back arrow" /></a
        >
      </div>
      <div class="left">
        <div class="left-container">
          <div>
            <p class="champion-name">{Championdata.Name}</p>
            <img
              class="ChampionImg"
              alt="BardImg"
              src="ChampThumbnails/{toBg(Championdata.Name)}.webp"
            />
          </div>

          <div class="BestItems">
            <p class="SubTitle">Best Items</p>
            <div class="BestItemsImgs">
              <!-- svelte-ignore a11y-mouse-events-have-key-events -->
              {#each Championdata.BestItems as itm, i}
                <div style="width: 41px; height:41px;">
                  <a href="items" rel="external">
                    {#if i == 0}
                      <div style="position:relative;">
                        <img
                          class="ItemImg"
                          alt="ItemImg"
                          src="items/{itm}.webp"
                          on:mouseover={hover1}
                          on:mouseleave={leave1}
                        />
                        <ItemDetails
                          {itemData}
                          name={Championdata.BestItems[0]}
                          hidden={!hover1x}
                          inCdetails={true}
                        />
                      </div>
                    {/if}
                    {#if i == 1}
                      <div style="position:relative;">
                        <img
                          class="ItemImg"
                          alt="ItemImg"
                          src="items/{itm}.webp"
                          on:mouseover={hover2}
                          on:mouseleave={leave2}
                        />
                        <ItemDetails
                          {itemData}
                          name={Championdata.BestItems[1]}
                          hidden={!hover2x}
                          inCdetails={true}
                        />
                      </div>
                    {/if}
                    {#if i == 2}
                      <div style="position:relative;">
                        <img
                          class="ItemImg"
                          alt="ItemImg"
                          src="items/{itm}.webp"
                          on:mouseover={hover3}
                          on:mouseleave={leave3}
                        />
                        <ItemDetails
                          {itemData}
                          name={Championdata.BestItems[2]}
                          hidden={!hover3x}
                          inCdetails={true}
                        />
                      </div>
                    {/if}
                  </a>
                </div>
              {/each}
            </div>
          </div>

          <div class="Stats">
            <p class="SubTitle">Champion Stats</p>
            <div class="StatsContainer">
              <p class="SmallSubtitles">Cost : {Championdata.Cost}</p>
              <p class="SmallSubtitles">Health : {Championdata.Health}</p>
              <p class="SmallSubtitles">Damage : {Championdata.Damage}</p>
              <p class="SmallSubtitles">Mana : {Championdata.Mana}</p>
              <p class="SmallSubtitles">
                Attack Speed : {Championdata.Attack_Speed}
              </p>
              <p class="SmallSubtitles">Armor : {Championdata.Armor}</p>
              <p class="SmallSubtitles">
                Magic Resist : {Championdata.Magic_Resist}
              </p>
              <p class="SmallSubtitles">Range : {Championdata.Range}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="right">
        <div class="right-top">
          <div class="right-top-container">
            <p class="BigTitle">Champion Abilities</p>
            <div class="AbilityContainer">
              <img
                class="AbilityImg"
                alt="BardImg"
                src="ChampAbilities/{toBg(Championdata.AbilityName)}.webp"
              />
              <!-- Ezt a képet kell kicserélni -->
              <p
                class="SubTitle"
                style="align-items: center; display: flex; margin-left: 20px;"
              >
                {Championdata.AbilityName}
              </p>
            </div>
            <div class="AbilityDescription">
              {Championdata.AbilityDescription}
            </div>
          </div>
        </div>
        <div class="right-bottom">
          <div class="right-bottom-container">
            <p class="BigTitle">Champion Traits & Synergies</p>
            <div class="traitContainer">
              {#each Championdata.Traits as tr}
                <div class="ChampTraits">
                  <div style="display: flex; align-items:center; gap: 6px">
                    <Trait name={tr.Name} traitData={findTrait(tr.Name)} />
                  </div>
                  <div class="TraitsChampions">
                    {#if tr.Champions.length > 1}
                      {#each tr.Champions as trc}
                        <a
                          href="/champions/{toBg(trc)}"
                          rel="external"
                          style="height: 54px; width:54px"
                        >
                          <Champ
                            actualNamename={getActual(trc)}
                            AllChampions={AllChamp}
                            {itemData}
                            name={toBg(trc)}
                            Items={[]}
                            cost={determineValue(trc)}
                            ThreeStar={false}
                          />
                        </a>
                      {/each}
                    {/if}
                  </div>
                </div>
              {/each}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</PageLayout>

<style>
  .arrowContainer {
    text-align: left;
    width: 340px;
    height: 40px;
    display: none;
  }
  .traitContainer {
    display: flex;
    flex-direction: column;
    gap: 22px;
  }
  .TraitsChampions {
    display: flex;
    flex-wrap: wrap;
    gap: 14px;
  }
  p {
    font-size: 24px;
    margin: 0;
    padding: 0;
    color: white;
  }
  .BigTitle {
    margin: 0;
    margin-bottom: 22px;
    padding: 0;
    color: white;
    font-weight: 600;
    font-size: 32px;
    line-height: 48px;
  }
  .champion-name {
    margin: 0;
    padding: 0;
    color: white;
    margin: 0;
    padding: 0;
    font-weight: 600;
    font-size: 28px;
    line-height: 42px;
  }
  .SubTitle {
    margin: 0;
    padding: 0;
    color: white;
    font-weight: 600;
    font-size: 24px;
    /* margin-bottom: 15px; */
    /* margin-top: 20px; */
  }
  .SmallSubtitles {
    color: white;
    font-weight: 600;
    font-size: 18px;
    line-height: 27px;
    margin: 0 !important;
    padding: 0;
    /* margin-bottom: 10px; */
  }
  .container {
    /* background-color: red; */
    margin-top: 200px;
    width: 1000px;
    display: flex;
    height: 100%;
    gap: 10px;
  }

  .left {
    /* background-color: green; */
    border: 1px solid #5e5d5d;
    width: 264px;
    height: 625px;
  }
  .left-container {
    padding: 15px;
  }
  .ChampionImg {
    width: 100%;
    height: 186px;
  }

  .BestItems {
    margin-top: 20px;
  }
  .BestItemsImgs {
    display: flex;
    justify-content: left;
    gap: 10px;
    margin-bottom: 10px;
  }
  .ItemImg {
    width: 41px;
    height: 41px;
  }
  .Stats {
    margin-top: 20px;
  }
  .right {
    /* background-color: aqua; */
    width: 716px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .right-top {
    /* background-color: brown; */
    border: 1px solid #5e5d5d;
    width: 100%;
  }

  .right-top-container {
    padding: 15px;
  }
  .AbilityContainer {
    display: flex;
  }
  .AbilityImg {
    width: 53px;
    height: 53px;
  }
  .AbilityDescription {
    margin-top: 10px;
    width: 100%;
    color: white;
    white-space: pre-line;
  }
  .right-bottom {
    /* background-color: white; */
    border: 1px solid #5e5d5d;
    width: 100%;
  }
  .right-bottom-container {
    padding: 15px;
    padding-bottom: 20px;
  }

  .ChampTraits {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .TraitsChampions {
    display: flex;
    grid-area: 8px;
  }

  @media (max-width: 1100px) {
    .container {
      flex-direction: column;
      align-items: center;
      width: 730px;
    }

    .left {
      height: 280px;
      width: 716px;
    }

    .left-container {
      justify-content: space-between;
      display: flex;
      flex-direction: row;
      height: 280px;
    }

    .BestItems {
      margin-top: 0;
      font-size: 28px;
    }

    .Stats {
      margin-top: 0;
    }
  }

  @media (max-width: 800px) {
    .container {
      flex-direction: column;
      align-items: center;
      width: 520px;
    }
    .left {
      width: 520px;
      height: 280px;
    }

    .ChampionImg {
      width: 230px;
    }

    .left-container {
      justify-content: space-around;
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      height: 300px;
    }
    .right {
      width: 520px;
    }
    .ChampTraits {
      flex-direction: column;
      align-items: flex-start;
      gap: 8px;
    }

    .BestItems {
      display: none;
    }
  }

  @media (max-width: 560px) {
    .arrowContainer {
      display: block;
    }
    .container {
      flex-direction: column;
      align-items: center;
      width: 340px;
      margin-top: 160px;
    }
    .left {
      width: 340px;
      height: 620px;
    }

    .ChampionImg {
      width: 230px;
    }

    .left-container {
      display: flex;
      flex-direction: column;
      height: 598px;
    }
    .right {
      width: 340px;
    }
    .ChampTraits {
      flex-direction: column;
      align-items: flex-start;
      gap: 12px;
    }

    .BestItems {
      margin-top: 12px;
      display: block;
    }

    .Stats {
      margin-top: 12px;
    }
    .BigTitle {
      font-size: 26px;
      line-height: 1.2;
    }
  }
</style>
