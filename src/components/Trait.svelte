<script>
  import TraitDetails from "./TraitDetails.svelte";

  export let name;
  export let traitData;

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

  let hoverx = false;

  function hover() {
    setTimeout(() => {
      hoverx = true;
    }, 250);
  }

  function leave() {
    setTimeout(() => {
      hoverx = false;
    }, 250);
  }
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div>
  <div on:mouseover={hover} on:mouseleave={leave}>
    <img
      src="./Traits/{traitChange(name)}.webp"
      alt={name}
      height="30"
      width="30"
    />
    <p>{name}</p>
  </div>
  <TraitDetails
    {name}
    description={traitData.Description}
    bonuses={traitData.Bonus}
    hidden={!hoverx}
  />
</div>

<style>
  div {
    width: 220px;
    position: relative;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  p {
    color: white;
    margin: 0;
    margin-right: 12px;
    font-size: 24px;
  }
</style>
