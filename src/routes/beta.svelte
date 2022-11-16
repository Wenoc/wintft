<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("traitData.json");
    const TraitData = await res.json();

    return { TraitData };
  }
</script>

<script>
  export let TraitData;
  import TraitDetails from "../components/TraitDetails.svelte";
</script>

<div>
  <TraitDetails
    name={TraitData[0].Name}
    description={TraitData[0].Description}
    bonuses={TraitData[0].Bonus}
  />
</div>

<style>
  div {
    margin-top: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
