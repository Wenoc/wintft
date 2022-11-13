<script>
  export let items;

  export let name;
  export let bg;

  if (name == "leesin") {
    name = "Lee Sin";
  }

  export let traits;
  export let cost;
</script>

<div class="opacity">
  <div
    class="champCard"
    style="background: linear-gradient(rgba(0,0,0,.5), rgba(0,0,0,0.5)), url('/ChampThumbnails/{bg}.jpg') top/cover"
  >
    <div class="cardLeft">
      <div class="leftUp">
        <div class="champTraits">
          {#each traits as trait}
            <div class="traitItem">
              <img
                src="./Traits/Set7_{trait}_w.svg"
                alt={trait}
                loading="lazy"
                decoding="async"
                height="30"
                width="30"
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
          {#each items as item}
            <img
              src="./items/{item}.webp"
              alt={item}
              loading="lazy"
              decoding="async"
            />
          {/each}
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  p {
    margin: 0;
    padding: 0;
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
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .cardLeft {
    height: 100%;
    width: 100%;
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
    height: 30px;
    margin-right: 6px;
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
      width: 22px;
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
