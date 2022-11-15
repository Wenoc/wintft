<script>
  import ItemDetails from "./ItemDetails.svelte";
  export let items;

  export let itemData;
  export let name;
  export let bg;

  if (name == "leesin") {
    name = "Lee Sin";
  }

  function traitChange(t) {
    t = t.replaceAll(" ", "");
    t = t.toLowerCase();
    if (t == "Underground") {
      return "theunderground";
    } else if (t == "Mecha:PRIME") {
      return "mechaprime";
    } else {
      return t;
    }
  }

  function changeName(nm) {
    nm = nm.replaceAll("-", "");
    nm = nm.replaceAll("'", "");
    return nm;
  }

  function toLink(nm) {
    nm = nm.replaceAll("-", "");
    nm = nm.replaceAll("'", "");
    nm = nm.replaceAll("", "");
    nm = nm.toLowerCase();
    return nm;
  }

  export let traits;
  export let cost;

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
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div class="opacity">
  <a href="champions/{toLink(name)}">
    <div
      class="champCard"
      style="background: linear-gradient(rgba(0,0,0,.5), rgba(0,0,0,0.5)), url('/ChampThumbnails/{changeName(
        bg
      )}.webp') top/cover"
    >
      <div class="cardLeft">
        <div class="leftUp">
          <div class="champTraits">
            {#each traits as trait}
              <div class="traitItem">
                <img
                  src="./Traits/{traitChange(trait)}.webp"
                  alt={trait}
                  loading="lazy"
                  decoding="async"
                />
                <p>{trait}</p>
              </div>
            {/each}
          </div>
        </div>
        <div class="leftDown" style="position: relative;">
          <p class="champName" style="padding-left: 6px;">{name}</p>
        </div>
      </div>
      <div class="cardRight">
        <div class="rightUp">
          <div class="champCost">
            <img
              src="coins.svg"
              alt="coin"
              decoding="async"
              height="20"
              width="20"
              loading="lazy"
            />
            <p>{cost}</p>
          </div>
        </div>
        <div class="rightDown">
          <div class="champItems">
            {#each items as item, i}
              {#if i == 0}
                <div class="itmDetail">
                  <img
                    src="items/{item}.webp"
                    alt={item}
                    loading="lazy"
                    decoding="async"
                    on:mouseover={hover1}
                    on:mouseleave={leave1}
                  />
                  <ItemDetails
                    {itemData}
                    name={items[0]}
                    hidden={!hover1x}
                    cc={true}
                  />
                </div>
              {/if}
              {#if i == 1}
                <div class="itmDetail">
                  <img
                    src="items/{item}.webp"
                    alt={item}
                    loading="lazy"
                    decoding="async"
                    on:mouseover={hover2}
                    on:mouseleave={leave2}
                  />
                  <ItemDetails
                    {itemData}
                    name={items[1]}
                    hidden={!hover2x}
                    cc={true}
                  />
                </div>
              {/if}
              {#if i == 2}
                <div class="itmDetail">
                  <img
                    src="items/{item}.webp"
                    alt={item}
                    loading="lazy"
                    decoding="async"
                    on:mouseover={hover3}
                    on:mouseleave={leave3}
                  />
                  <ItemDetails
                    {itemData}
                    name={items[2]}
                    hidden={!hover3x}
                    cc={true}
                  />
                </div>
              {/if}
            {/each}
          </div>
        </div>
      </div>
    </div>
  </a>
</div>

<style>
  .itmDetail {
    position: relative;
    display: flex;
    align-items: flex-end;
  }
  p {
    margin: 2px;
    padding: 0;
    font-size: 18px;
  }

  .champCard {
    border: 1px solid #202020;
    color: white;
    height: 180px;
    width: 300px;
    padding: 5px;
    border-radius: 4px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .cardRight {
    height: 100%;
    width: 40%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .cardLeft {
    height: 100%;
    width: 60%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .leftUp {
    height: 100%;
    width: 100%;
  }

  .leftDown {
    height: 100%;
    width: 100%;
  }

  .rightUp {
    position: relative;
    height: 100%;
    width: 100%;
  }

  .rightDown {
    height: 100%;
    width: 100%;
    position: relative;
  }

  .traitItem {
    display: flex;
    justify-content: start;
    align-items: center;
    font-size: 16px;
    font-weight: 600;
  }

  .traitItem img {
    height: 24px;
    margin-right: 6px;
    margin-left: 4px;
  }

  .champName {
    position: absolute;
    bottom: 0;
    font-size: 22px;
  }

  .champCost {
    position: absolute;
    right: 0;
    display: flex;
    justify-content: start;
    align-items: center;
    padding-right: 6px;
    gap: 4px;
  }

  .champCost img {
    height: 20px;
  }

  .champItems {
    position: absolute;
    bottom: 0;
    right: 0;
    padding-right: 4px;
    padding-bottom: 4px;
    display: flex;
    justify-content: start;
    align-items: center;
    gap: 4px;
  }

  .champItems img {
    height: 26px;
  }

  .champTraits {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 2px;
  }

  @media (max-width: 800px) {
    .champCard {
      width: 160px;
      height: 112px;
    }

    .champName {
      font-size: 16px;
    }

    .traitItem {
      height: 22px;
    }

    .traitItem img {
      height: 18px;
    }

    .traitItem p {
      font-size: 13px;
    }

    .champItems {
      padding-right: 0px;
      padding-bottom: 0px;
    }

    .champItems img {
      width: 20px;
      height: 20px;
    }

    .champCost img {
      width: 18px;
      height: 22px;
    }
    .cardRight {
      width: 50%;
    }
  }
</style>
