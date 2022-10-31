<script>
  import Header from "../components/Header.svelte";
  import PageLayout from "../components/PageLayout.svelte";
</script>

<svelte:head>
  <title
    >TFT Comp Comps, Guides and More for Patch 12.20b, Set 7.5 - WinTFT</title
  >
  <meta
    name="description"
    content="WinTFT helps you with TFT Team Compositions and guides so that you'll always be able to start your games one step ahead of your opponents."
  />
</svelte:head>

<PageLayout>
  <div slot="middle" style="margin-bottom: 100px;">
    <Header
      headerText="A website for TFT team comps and guides"
      home={true}
      description={true}
    />
    <div class="element1">
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div class="textCon">
          <h1>
            <a rel="external" href="team-comps" style="text-decoration: none;"
              >Team Comps</a
            >
          </h1>
          <p style="color: #727070;">
            There are various team comps on the site. Every comp comes with a
            general guideline, and some comps have an in-depth guide.
          </p>
        </div>
      </div>
      <div class="imgCon">
        <img src="compimg.png" alt="exaple of a comp" width="600" />
      </div>
    </div>
    <div class="element2">
      <div class="imgCon">
        <img src="aag1.png" alt="exaple of a augments" width="600" />
      </div>
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div class="textCon">
          <h1>
            <a rel="external" href="augments" style="text-decoration: none;"
              >Augments</a
            >
          </h1>
          <p style="color: #727070;">
            All augments in the game are on this page. You can read what it does
            and see how good it is compared to the other augments.
          </p>
        </div>
      </div>
    </div>
    <div class="element1">
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div class="textCon">
          <h1>
            <a rel="external" href="champions" style="text-decoration: none;"
              >Champions</a
            >
          </h1>
          <p style="color: #727070;">
            Every champion from TFT is here. You can see the champions' traits,
            cost, and best items.
          </p>
        </div>
      </div>
      <div class="imgCon">
        <img src="champimg.webp" alt="exaple of a comp" width="600" />
      </div>
    </div>
    <div class="element2">
      <div class="imgCon">
        <img src="blogimg.webp" alt="exaple of a augments" width="600" />
      </div>
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div class="textCon">
          <h1>
            <a rel="external" href="guides" style="text-decoration: none;"
              >Guides</a
            >
          </h1>
          <p style="color: #727070;">
            There are a few comp-specific and general guides on the site for you
            to improve at the game.
          </p>
        </div>
      </div>
    </div>
  </div>
  <div slot="right" />
  <div slot="left" />
</PageLayout>

<style>
  .element1 {
    margin-top: 130px;
    display: flex;
    width: 1000px;
    gap: 20px;
  }

  .imgCon {
    width: 100%;
    text-align: center;
  }

  .element2 {
    gap: 20px;
    margin-top: 130px;
    display: flex;
    width: 1000px;
    text-align: right;
  }

  h1 {
    color: white;
    font-weight: bold;
  }

  @media (max-width: 1200px) {
    .element1 {
      flex-direction: column;
      width: 700px;
    }
    .element2 {
      flex-direction: column-reverse;
      width: 700px;
    }
    h1 {
      text-align: center;
    }
    p {
      text-align: center;
    }
    .textCon {
      width: 600px;
    }

    .imgCon {
      width: 100%;
      text-align: center;
    }

    @media (max-width: 750px) {
      .element1 {
        flex-direction: column;
        width: 350px;
      }
      .element2 {
        flex-direction: column-reverse;
        width: 350px;
      }
      .imgCon img {
        width: 350px;
      }
    }
  }
</style>
