<script context="module">
    export async function preload(page, session) {
    const res = await this.fetch("championdata/Alistar.json");
    const Championdata = await res.json();
    return {Championdata};
  }
</script>

<script>
  import { each } from "svelte/internal";

    import PageLayout from "../../components/PageLayout.svelte";

    export let Championdata;
</script>

<PageLayout>
    <div slot="middle" style="margin-top: 200px; width: 1000px;">
        <div class="container">
            <div class="left">
                <div class="left-container">
                    <p class="champion-name">{Championdata.Name}</p>
                    <img class="ChampionImg" alt="BardImg" src="ChampThumbnails/bard.jpg" />

                    <div class="BestItems">
                        <p class="SubTitle">Best Items</p>
                        <div class="BestItemsImgs">
                            <img class="ItemImg" alt="ItemImg" src="items/bow.webp" />
                            <img class="ItemImg" alt="ItemImg" src="items/bow.webp" />
                            <img class="ItemImg" alt="ItemImg" src="items/bow.webp" />
                        </div>
                    </div>

                    <div class="Stats">
                        <p class="SubTitle">Champion Stats</p>
                        <div class="StatsContainer">
                            <p class="SmallSubtitles">Const : {Championdata.Cost}</p>
                            <p class="SmallSubtitles">Health : {Championdata.Health}</p>
                            <p class="SmallSubtitles">Damage : {Championdata.Damage}</p>
                            <p class="SmallSubtitles">Mana : {Championdata.Mana}</p>
                            <p class="SmallSubtitles">Attack Speed : {Championdata.Attack_Speed}</p>
                            <p class="SmallSubtitles">Armor : {Championdata.Armor}</p>
                            <p class="SmallSubtitles">Magic Resist : {Championdata.Magic_Resist}</p>
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
                            <img class="AbilityImg" alt="BardImg" src="ChampThumbnails/bard.jpg" /> <!-- Ezt a képet kell kicserélni -->
                            <p class="SubTitle" style="align-items: center; display: flex; margin-left: 30px;">{Championdata.AbilityName}</p>
                        </div>
                        <div class="AbilityDescription">
                            {Championdata.AbilityDescription}
                        </div>
                    </div>
                </div>
                <div class="right-bottom">
                    <div class="right-bottom-container">
                        <p class="BigTitle">Champion Traits & Synergies</p>
                        <div>
                            {#each Championdata.Traits as tr}
                                <div class="ChampTraits">
                                    <img alt="CharacterIcons" class="TraitsIcon" src="Traits/hacker.webp" />
                                    <p>{tr.Name}</p>
                                    <div class="TraitsChampions">
                                        {#each tr.Champions as trc}
                                            <p>{trc}</p>
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
    p {
        font-size: 24px;
        margin: 0;
        padding: 0;
        color: white;
    }
    .BigTitle {
        margin: 0;
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
        display: flex;
        height: 100%;
        gap: 10px;
    }

    .left {
        /* background-color: green; */
        border: 1px solid #5E5D5D;
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
    .champion-name {
        /* text-align: center; */
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
        border: 1px solid #5E5D5D;
        width: 100%;
    }

    .right-top-container {
        padding: 15px;
    }
    .AbilityContainer {
        display: flex;
        margin-top: 30px;
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
        border: 1px solid #5E5D5D;
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
</style>