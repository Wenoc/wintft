<script context="module">
  export async function preload(page, session) {
        const res = await this.fetch('/data.json');
        const AllChampions = await res.json();
  
        const res2 = await this.fetch('/compData.json');
        const compData = await res2.json();
        let combine = [];

        const res3 = await this.fetch('/augmentData.json');
        const augmentData = await res3.json();
        combine[0] = AllChampions;
        combine[1] = compData;
        combine[2] = augmentData;

        return {combine};
  }
</script>


<script>
  import Header from "../components/Header.svelte";
  import NewComp from "../components/newComp.svelte";
  
  export let combine;
  let AllChampions = combine[0];
  let compData = combine[1];
  let augmentData = combine[2];

  function reverseComp(comp){
    let reversed = Object.values(comp)
    reversed = reversed.reverse();
    return reversed;
  }

</script>

<div>
  <div style="text-align: center;">
     <Header headerText="Team Comps"/>
     <div></div>
     <div style="display: flex; justify-content:center">
      <div class="compsContainer">
        <div class="patchInfo" style="margin-bottom: 20px;">
           <div>
              <div class="blockContainer">
                 <p style="padding: 0; margin: 0;">Set 7</p>
              </div>
              <div class="blockContainer">
                 <p style="padding: 0; margin: 0;">Patch 12.2</p>
              </div>
           </div>
           <div class="blockContainer">
              <p style="padding: 0; margin: 0;">Last updated: 19, Aug 2022</p>
           </div>
        </div>
        {#each compData as comp}
          <NewComp {augmentData} {AllChampions} threeStar={comp.threeStar} id={comp.id} name={comp.name} tier={comp.tier} champions={reverseComp(comp.champions)} carousel={comp.carousel} augments={comp.augments} lvl9={comp.lvl9} optionsChampionsRight={comp.optionsChampionsRight} optionsChampionsLeft={comp.optionsChampionsLeft}
              Gtraits={comp.traits[0].gold} Straits={comp.traits[1].silver} Btraits={comp.traits[2].bronze} difficulty={comp.difficulty} type={comp.type} carries={comp.carries} positions={comp.positions}/>
        {/each}
     </div>
     </div>
  </div>
</div>


<style>

      .compsContainer{
        max-width: 980px;
      }
      @media(max-width:1200px){
        .compsContainer{
          max-width: 83%;
        }
      }
      @media(max-width:580px){
        .patchInfo{
          flex-direction: column;
          gap:15px
        }
          .compsContainer{
            width: 90%
        }
      }
      
    .patchInfo{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .patchInfo div:nth-child(1){
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
</style>
