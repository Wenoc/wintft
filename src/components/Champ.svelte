<script>
  import { onMount } from "svelte";
  import ItemDetails from "./ItemDetails.svelte";
  import ChampDetails from "./champDetails.svelte";

  export let itemData;
  export let name;
  export let Items = [];
  export let ThreeStar = false;
  export let augment = false;
  export let AllChampions;
  export let actualNamename;

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

  let hover1x = false;

  function hover1() {
    setTimeout(() => {
      hover1x = true;
    }, 250);
  }

  function leave1() {
    setTimeout(() => {
      hover1x = false;
    }, 250);
  }

  let hover2x = false;

  function hover2() {
    setTimeout(() => {
      hover2x = true;
    }, 250);
  }

  function leave2() {
    setTimeout(() => {
      hover2x = false;
    }, 250);
  }

  let hover3x = false;

  function hover3() {
    setTimeout(() => {
      hover3x = true;
    }, 250);
  }

  function leave3() {
    setTimeout(() => {
      hover3x = false;
    }, 250);
  }

  let hover1xy = false;

  function hover1y() {
    setTimeout(() => {
      hover1xy = true;
    }, 250);
  }

  function leave1y() {
    setTimeout(() => {
      hover1xy = false;
    }, 250);
  }
  let opt = false;
  if (actualNamename == 0) {
    opt = true;
  }
</script>

<div style="position: relative;" id="max">
  <ChampDetails
    hidden={!hover1xy}
    {AllChampions}
    {name}
    {actualNamename}
    {opt}
  />
  <div
    class="champContainer"
    class:augment
    class:noaugment={!augment}
    style="outline: 3px solid {borderColor};"
  >
    <!-- svelte-ignore a11y-mouse-events-have-key-events -->
    <img
      src="ChampIcons/tft8_{name}.webp"
      alt={name}
      loading="lazy"
      decoding="async"
      style="max-width:100%;"
      on:mouseover={hover1y}
      on:mouseleave={leave1y}
    />
  </div>
  <div class="stars" class:dontShow={!ThreeStar}>
    <div style="position: relative;">
      <img
        src="star.svg"
        alt={name}
        loading="lazy"
        decoding="async"
        style="position: absolute; left: -55px;"
      />
      <img
        src="star.svg"
        alt={name}
        loading="lazy"
        decoding="async"
        style="position: absolute; left: -40px;"
      />
      <img
        src="star.svg"
        alt={name}
        loading="lazy"
        decoding="async"
        style="position: absolute; left: -25px;"
      />
    </div>
  </div>
  <div
    class="items"
    class:items2={Items.length == 2}
    class:items3={Items.length == 1}
  >
    {#if Items.length > 0}
      {#each Items as item, i}
        <!-- svelte-ignore a11y-mouse-events-have-key-events -->
        {#if i == 0}
          <img
            src="items/{item}.webp"
            alt={item}
            loading="lazy"
            decoding="async"
            on:mouseover={hover1}
            on:mouseleave={leave1}
          />
        {/if}
        {#if i == 1}
          <!-- svelte-ignore a11y-mouse-events-have-key-events -->
          <img
            src="items/{item}.webp"
            alt={item}
            loading="lazy"
            decoding="async"
            on:mouseover={hover2}
            on:mouseleave={leave2}
          />
        {/if}
        {#if i == 2}
          <!-- svelte-ignore a11y-mouse-events-have-key-events -->
          <img
            src="items/{item}.webp"
            alt={item}
            loading="lazy"
            decoding="async"
            on:mouseover={hover3}
            on:mouseleave={leave3}
          />
        {/if}
      {/each}
      <ItemDetails {itemData} name={Items[0]} hidden={!hover1x} />
      {#if Items[1] != undefined}
        <ItemDetails {itemData} name={Items[1]} hidden={!hover2x} />
      {/if}
      {#if Items[2] != undefined}
        <ItemDetails {itemData} name={Items[2]} hidden={!hover3x} />
      {/if}
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
