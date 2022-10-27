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
    content="If you want to improve in TFT or try something new, check out our site.
    We provide the best TFT team comps in every patch and often publish guides to help you get better at the game."
  />
</svelte:head>

<PageLayout>
  <div slot="middle" style="margin-bottom: 100px;">
    <Header
      headerText="The best website for TFT team comps and guides"
      home={true}
      description={true}
    />
    <div class="element1">
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div>
          <h1>Team Comps</h1>
          <p style="color: #727070;">
            There are various team comps on the site. Every comp comes with a
            general guideline and some comps have an in-dept guide attached to
            them.
          </p>
        </div>
      </div>
      <div style="width: 100%;">
        <img src="tc1.png" alt="exaple of a comp" width="600" />
      </div>
    </div>
    <div class="element2">
      <div style="width: 100%;">
        <img src="aag1.png" alt="exaple of a augments" width="600" />
      </div>
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div>
          <h1>Augments</h1>
          <p style="color: #727070;">
            If you can't decide what augment to pick or what an augment does,
            this page got you covered.
          </p>
        </div>
      </div>
    </div>
    <div class="element1">
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div>
          <h1>Champions</h1>
          <p style="color: #727070;">
            There is a page on the site, which has all the champs in the game.
            It shows the unit's cost, traits, and the best items for it.
          </p>
        </div>
      </div>
      <div style="width: 100%;">
        <img src="cah1.png" alt="exaple of a comp" width="600" />
      </div>
    </div>
    <div class="element2">
      <div style="width: 100%;">
        <img src="ga.png" alt="exaple of a augments" width="600" />
      </div>
      <div
        style="width: 100%; display:flex; justify-content:center; align-items:center"
      >
        <div>
          <h1>Guides</h1>
          <p style="color: #727070;">
            The site has high quality guides. <br /> There are comp specific and
            also general guides for you to improve at the game.
          </p>
        </div>
      </div>
    </div>
  </div>
  <div slot="right">a</div>
  <div slot="left">a</div>
</PageLayout>

<style>
  .element1 {
    margin-top: 130px;
    display: flex;
    width: 1000px;
    gap: 20px;
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
</style>
