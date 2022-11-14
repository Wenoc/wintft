<script>
  export let isSecond = false;
  export let name = "";
  export let Description = "";
  export let src = "";
</script>

<div class="augment" class:second={isSecond}>
  <div class="container">
    <div class="section nameSec">
      <div class="augmentNameSection" style="padding-left: 10px;">
        <div
          style="display: flex; justify-content: start; align-items: center; min-height: 73px;"
        >
          <div class="augImg">
            <img
              src="/augments/{src}.png"
              alt={name}
              decoding="async"
              style="height: 100%; width:100%"
              loading="lazy"
            />
          </div>
          <div>
            <p>{name}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="section descriptionx">
      <div style="padding-left: 10px;">
        <p class="description">{Description}</p>
      </div>
    </div>
  </div>
</div>

<style>
  .augImg {
    width: 60px;
    padding-top: 6px;
  }

  .nameSec {
    width: 30%;
    text-align: left;
  }

  .descriptionx {
    width: 70%;
    text-align: left;
  }
  .container {
    display: flex;
    flex: 1 1 auto;
    min-height: 50px;
  }

  .augment {
    font-weight: 500;
    font-size: 18px;
    display: flex;
    background-color: #22242f;
    color: white;
    justify-content: center;
    align-items: center;
    border: 1px solid #5e5d5d;
    border-top: 0;
    border-right: 0;
    min-height: 73px;
  }

  .augment .section {
    border-right: 1px solid #5e5d5d;
    font-weight: normal;
    display: flex;
    justify-content: start;
    align-items: center;
    flex: 1 1 auto;
  }

  .augmentNameSection {
    display: flex;
    justify-content: start;
    align-items: center;
  }

  p {
    margin: 9px;
  }

  .second {
    background-color: #2d2f3a;
  }

  .description {
    font-size: 14px;
  }

  @media (max-width: 1100px) {
    .descriptionx {
      display: none;
    }
    .augment div:nth-child(3) {
      display: none;
    }
    .nameSec {
      width: 70%;
    }
  }

  @media (max-width: 700px) {
    p {
      font-size: 14px;
    }
    .augImg {
      width: 50px;
    }

    .nameSec {
      width: 90%;
    }
  }
</style>
