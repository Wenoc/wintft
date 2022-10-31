<script>
  export let headerText;
  export let description = false;
  export let home = false;
  export let text =
    "WinTFT helps you with Team Compositions and guides so that you'll always be able to start your games one step ahead of your opponents";
  if (description == false) {
    text = "";
  }
</script>

<div style="" class="wrapAll">
  <div class="up">
    <div class="brandtext" style="text-align: right;">
      <img
        src="finalbrand.png"
        alt=""
        height="96"
        style="margin-bottom: 14px;"
      />
    </div>
    <div class="svgContainer">
      <svg id="chart" width="1" height="50">
        <line x1="20" y1="20" x2="20" y2="130" />
      </svg>
    </div>
    <div class="headerTextContainer">
      <h1 class="mainText" class:homepage={home}>
        {headerText}
      </h1>
    </div>
  </div>
  <div class="down" style="margin-top: 10px;">
    <p>{text}</p>
  </div>
</div>

<style>
  .wrapAll {
    margin-top: 134px;
    margin-bottom: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .headerTextContainer {
    margin-left: 28px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .svgContainer {
    padding-top: 5px;
  }
  .up {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .mainText {
    color: white;
    font-size: 40px;
    line-height: 30px;
    max-width: 300px;
    width: 300px;
    text-align: start;
  }
  svg#chart {
    background: #b97331;
    width: 3px;
  }

  .down p {
    color: gray;
    text-align: center;
    max-width: 630px;
    margin-top: 0;
    font-weight: 500;
  }
  .brandtext {
    display: flex;
    justify-content: end;
    align-items: center;
    margin-right: 28px;
    width: 240px;
    height: 70px;
  }
  @media (max-width: 1000px) {
    .up {
      flex-direction: column;
    }

    .svgContainer {
      display: none;
    }
    .brandtext {
      display: none;
    }

    .mainText {
      font-size: 36px;
      text-align: center;
    }

    .headerTextContainer {
      margin: 0;
    }
  }

  h1 {
    font-size: 36px;
    font-weight: 700;
    margin-bottom: 0%;
  }

  p {
    margin: 0;
    padding-bottom: 6px;
  }
  .homepage {
    font-size: 24px;
  }

  @media (max-width: 750px) {
    .homepage {
      font-size: 30px;
      line-height: 32px;
    }
    .down {
      display: none;
    }
  }
</style>
