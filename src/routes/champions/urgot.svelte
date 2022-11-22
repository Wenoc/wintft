<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("championdata/Urgot.json");
    const Championdata = await res.json();

    const res2 = await this.fetch("ChampData.json");
    const AllChamp = await res2.json();

    const res3 = await this.fetch("./ItemsData/itemData.json");
    const itemData = await res3.json();

    const res4 = await this.fetch("traitData.json");
    const traitData = await res4.json();

    const res5 = await this.fetch("./AugmentsData/carryAugments.json");
    const carryAugs = await res5.json();

    const res6 = await this.fetch("./AugmentsData/supportAugments.json");
    const supportAugments = await res6.json();

    let combine = [];
    combine[0] = Championdata;
    combine[1] = AllChamp;
    combine[2] = itemData;
    combine[3] = traitData;
    combine[4] = carryAugs;
    combine[5] = supportAugments;

    return { combine };
  }
</script>

<script>
  import ChampPage from "../../components/ChampPage.svelte";

  let carrya;
  let carryadesc;

  let suppa;
  let suppadesc;
  export let combine;
  function findCAug() {
    combine[4].forEach((element) => {
      if (element.Icon == combine[0].Name) {
        carrya = element.Name;
        carryadesc = element.Description;
      }
    });
  }

  function findSAug() {
    combine[5].forEach((element) => {
      if (element.Icon == combine[0].Name) {
        suppa = element.Name;
        suppadesc = element.Description;
      }
    });
  }

  findSAug();
  findCAug();
</script>

<ChampPage {combine} {carrya} {carryadesc} {suppa} {suppadesc} />
