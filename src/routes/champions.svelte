<script context="module">
    // console.log('module script');
    export async function preload(page, session) {
          const res = await this.fetch('/data.json');
          const AllChampions = await res.json();
  
          return { AllChampions };
    }
  </script>

<script>
import Champ from "../components/Champ.svelte";

    import ChampionsChamp from "../components/ChampionsChamp.svelte";
    import Header from "../components/Header.svelte";
    export let AllChampions;


</script>

<div>
    <Header />
    <div class="championsContainer">
        <div>
            {#each AllChampions as Champ}
                <ChampionsChamp name={Champ.name} traits={Champ.traits} items={Champ.items}/>
            {/each}
        </div>
    </div>
</div>


<style>
    .championsContainer div{
        max-width: 980px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        gap: 20px;
    }

    .championsContainer{
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
