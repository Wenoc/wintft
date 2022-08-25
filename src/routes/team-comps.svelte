<script context="module">
  // console.log('module script');
  export async function preload(page, session) {
        const res = await this.fetch('/data.json');
        const ChamionCost = await res.json();

        return { ChamionCost };
  }
</script>

<script>
  import PageLayout from "../components/PageLayout.svelte";
  import Header from "../components/Header.svelte";
  import SidePengu from "../components/SidePengu.svelte";
  import Comp from "../components/Comp.svelte";
  export let ChamionCost;
</script>

<div>
  <div style="text-align: center;">
     <Header />
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
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
        <Comp {ChamionCost} />
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
