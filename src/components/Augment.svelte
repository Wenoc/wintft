<script>
  export let isSecond = false;
  export let name = "";
  export let tier = "";
  export let Description = "";
  export let src = "";

  export let color;
</script>

<div class="augment" class:second={isSecond} id="outer">
  <div class="container">
    <div class="section nameSec">
      <div class="augmentNameSection" style="padding-left: 10px;">
        <div
          style="display: flex; justify-content: start; align-items: center; min-height: 73px;"
        >
          <div style="width: 60px; padding-top: 6px;">
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
    <div class="section tierSec" id="inner">
      <div style="display: flex; justify-content: center;">
        <div class="SLetter" style="margin: 6px 0; background-color: #{color};">
          <p style="border: 0; margin:0; padding:0;">{tier}</p>
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
  .nameSec {
    width: 30%;
    text-align: left;
  }

  .SLetter {
    height: 32px;
    width: 32px;
    background-color: #f05867;
    border-radius: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 25px;
    font-weight: 600;
    color: black;
  }
  .descriptionx {
    width: 60%;
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

  .tierSec {
    width: 10%;
    justify-content: center !important;
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
</style>
