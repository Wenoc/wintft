<script>
  export let name;
  export let Items = [];
  export let ThreeStar = false;
  export let augment = false;

  export let cost;

  let borderColor = "#878aa2";

  if (Items.length > 1) {
    for (let i = 0; i < Items.length; i++) {
      Items[i] = Items[i].replaceAll("'", "");
      Items[i] = Items[i].replaceAll(" ", "");
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
</script>

<div style="position: relative;">
  <div
    class="champContainer"
    class:augment
    class:noaugment={!augment}
    style="outline: 3px solid {borderColor};"
  >
    <img
      src="ChampIcons/{name}.png"
      alt={name}
      style="max-width:100%;"
      title={name}
    />
  </div>
  <div class="stars" class:dontShow={!ThreeStar}>
    <div style="position: relative;">
      <img src="star.svg" alt={name} style="position: absolute; left: -55px;" />
      <img src="star.svg" alt={name} style="position: absolute; left: -40px;" />
      <img src="star.svg" alt={name} style="position: absolute; left: -25px;" />
    </div>
  </div>
  <div
    class="items"
    class:items2={Items.length == 2}
    class:items3={Items.length == 1}
  >
    {#if Items.length > 0}
      {#each Items as item}
        <img src="items/{item}.png" alt={item} title={item} />
      {/each}
    {/if}
  </div>
</div>

<style>
  .augment {
    height: 40px;
    width: 40px;
  }

  .noaugment {
    height: 60px;
    width: 60px;
  }

  .champContainer {
    outline-offset: -3px;
    border-radius: 2px;
  }
  .stars img {
    width: 18px;
  }
  .stars {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: -10px;
    right: -2px;
  }

  .items img {
    width: 20px;
    border: 1px solid black;
  }

  .items {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 52px;
    right: -4px;
    gap: 1px;
  }

  .dontShow {
    display: none;
  }

  .items2 {
    right: 8px;
  }

  .items3 {
    right: 18px;
  }
</style>
