<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("championdata/Alistar.json");
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
  import ChampPage from "../../components/ChampPage.svelte";

  export let combine;
</script>

<ChampPage {combine} />
