<script>
  export let name;
  export let hidden = true;
  export let itemData;

  export let cc = false;
  export let inCdetails = false;

  let description;
  let actualName;

  let component1;
  let component2;

  for (let i = 0; i < itemData.length; i++) {
    if (itemData[i].icon == name) {
      actualName = itemData[i].name;
      description = itemData[i].description;
      component1 = itemData[i].component1;
      component2 = itemData[i].component2;
    }
  }

  if (name == undefined) {
    console.log(name);
  }

  let hoeverontext = false;

  function hoeverontextf() {
    hoeverontext = true;
  }
  function leaveontext() {
    setTimeout(() => {
      hoeverontext = false;
    }, 250);
  }
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div
  class="absoluteContainer"
  class:absoluteContainerChange={cc}
  class:inCdetails
>
  <div
    class="itemDetailContainer"
    class:hidden={hidden == true}
    on:mouseover={hoeverontextf}
    on:mouseleave={leaveontext}
  >
    <div class="up">
      <div class="left">
        <img
          src="items/{name}.webp"
          alt="ArchangelsStaff"
          height="50"
          width="50"
        />
      </div>
      <div class="right">
        <p>{actualName}</p>
        <div class="components">
          {#if component1 != ""}
            <img
              src="./items/{component1}.webp"
              alt={component1}
              height="28"
              width="28"
            />
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              height="24"
              width="24"
              ><g data-name="Layer 2"
                ><g data-name="plus"
                  ><rect
                    width="24"
                    height="24"
                    opacity="0"
                    transform="rotate(180 12 12)"
                  /><path
                    fill="white"
                    d="M19 11h-6V5a1 1 0 0 0-2 0v6H5a1 1 0 0 0 0 2h6v6a1 1 0 0 0 2 0v-6h6a1 1 0 0 0 0-2z"
                  /></g
                ></g
              ></svg
            >
            <img
              src="./items/{component2}.webp"
              alt={component2}
              height="28"
              width="28"
            />
          {:else}
            <span> Item Not Craftable </span>
          {/if}
        </div>
      </div>
    </div>
    <div class="down">
      <span>
        {description}
      </span>
    </div>
  </div>
</div>

<style>
  .inCdetails {
    top: 60px !important;
    right: -160px !important;
  }
  .hidden {
    display: none;
  }

  .absoluteContainer {
    position: absolute;
    bottom: 30px;
    z-index: 3;
  }

  .absoluteContainerChange {
    position: absolute;
    bottom: 40px !important;
    right: -170px !important;
  }

  .components {
    display: flex;
    flex-direction: row;
    gap: 4px;
    align-items: center;
    height: 100%;
  }
  .itemDetailContainer {
    width: 360px;
    height: auto;
    background-color: #22242f;
    border: 1px solid #5e5d5d;
  }
  .up {
    height: 70px;
    display: flex;
    flex-direction: row;
    border-bottom: 1px solid #5e5d5d;
  }

  .left {
    height: 100%;
    width: 70px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-right: 1px solid #5e5d5d;
  }

  .right {
    display: flex;
    flex-direction: column;

    padding-top: 6px;
    padding-left: 8px;
  }

  .down {
    padding: 6px 8px;
  }

  p {
    height: 40%;
    color: white;
    margin: 0;
    font-size: 15px;
  }

  span {
    white-space: pre-line;
    display: block;
    font-size: 14px;
    font-weight: 400;
    color: white;
    line-height: 1.6;
  }
  @media (max-width: 1350px) {
    .absoluteContainerChange {
      position: absolute;
      bottom: 40px !important;
      right: -60px !important;
    }
  }
  @media (max-width: 700px) {
    .absoluteContainer {
      display: none;
    }
  }
  @media (max-width: 800px) {
    .absoluteContainerChange {
      display: none;
    }
  }
</style>
