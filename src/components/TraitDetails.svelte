<script>
  export let name;
  export let description;
  export let bonuses;

  export let hidden;

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
</script>

<div class="traitContainer" class:hidden>
  <div class="up">
    <div class="top">
      <img src="./Traits/{traitChange(name)}.webp" alt="name" />
      <p class="title">{name}</p>
    </div>
    <p>{description}</p>
  </div>
  <div class="down">
    {#each bonuses as bonus}
      <div class="group">
        <div class="value">
          <p>{bonus.Value}</p>
        </div>
        <div class="disc">
          <span>{bonus.Desc}</span>
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  .hidden {
    display: none;
  }
  .top {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 6px;
    padding-top: 0px;
  }
  .title {
    font-weight: bold;
    font-size: 22px;
  }

  .group {
    display: flex;
    justify-content: start;
    gap: 12px;
    align-items: flex-start;
  }
  .value {
    margin-top: 4px;
    padding: 4px 18px;
    background-color: #13141b;
    border-radius: 3px;
  }
  .traitContainer {
    z-index: 5;
    position: absolute;
    bottom: 60px;
    right: -210px;
    width: 460px;
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
  }

  p {
    margin: 0;
    color: white;
    font-weight: 400;
  }

  .down {
    padding: 12px;
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .down span {
    color: white;
    font-size: 16px;
    font-weight: 400;
  }

  .up {
    border-bottom: 1px solid #5e5d5d;
    padding: 10px;
  }

  @media (max-width: 800px) {
    .traitContainer {
      display: none;
    }
  }
</style>
