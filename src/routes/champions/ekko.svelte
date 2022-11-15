<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("championdata/Ekko.json");
    const Championdata = await res.json();

    const res2 = await this.fetch("data.json");
    const AllChamp = await res2.json();

    let combine = [];
    combine[0] = Championdata;
    combine[1] = AllChamp;

    return { combine };
  }
</script>

<script>
  import PageLayout from "../../components/PageLayout.svelte";

  export let combine;
  let Championdata = combine[0];
  let AllChamp = combine[1];

  function toBg(x) {
    x = x.toLowerCase();
    x = x.replaceAll("'", "");
    x = x.replaceAll(" ", "");
    return x;
  }

  let borderColor = "#878aa2";

  function borderCol(ch) {
    let cost;
    for (let i = 0; i < AllChamp.length; i++) {
      if (AllChamp[i].Name == ch) {
        cost = AllChamp[i].Cost;
      }
    }

    if (cost == 1) {
      borderColor = "#878aa2";
    } else if (cost == 2) {
      borderColor = "#11b88e";
    } else if (cost == 3 || cost == 6) {
      borderColor = "#417deb";
    } else if (cost == 4 || cost == 7) {
      borderColor = "#c92a73";
    } else if (cost == 5 || cost == 8) {
      borderColor = "#f2c530";
    }

    return borderColor;
  }
</script>

<PageLayout>
  <div slot="middle">
    <div class="container">
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
              {#each Championdata.BestItems as itm}
                <img class="ItemImg" alt="ItemImg" src="items/{itm}.webp" />
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
                    <img
                      alt={tr.Name}
                      class="TraitsIcon"
                      src="Traits/{toBg(tr.Name)}.webp"
                    />
                    <p style="margin-right: 12px">{tr.Name}</p>
                  </div>
                  <div class="TraitsChampions">
                    {#each tr.Champions as trc}
                      <a href="/champions/{toBg(trc)}" rel="external">
                        <img
                          style="border: 2px solid {borderCol(trc)}"
                          src="ChampIcons/tft8_{toBg(trc)}.webp"
                          alt={trc}
                          height="50"
                        />
                      </a>
                    {/each}
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
  .traitContainer {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .TraitsChampions {
    display: flex;
    gap: 10px;
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
  }

  .ChampTraits {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .TraitsIcon {
    width: 30px;
    height: 30px;
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
      gap: 12px;
    }

    .BestItems {
      display: none;
    }
  }

  @media (max-width: 560px) {
    .container {
      flex-direction: column;
      align-items: center;
      width: 360px;
    }
    .left {
      width: 360px;
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
      width: 360px;
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
  }
</style>
