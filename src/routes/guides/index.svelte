<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch("/blogData.json");
    const augmentData = await res.json();

    return { augmentData };
  }
</script>

<script>
  import BlogItem from "../../components/BlogItem.svelte";
  import PageLayout from "../../components/PageLayout.svelte";

  export let augmentData;
  var kereses = "";
  let seachedAugments = augmentData;

  function augmentkereses() {
    return augmentData.filter(
      (line) =>
        line.title.toLowerCase().includes(kereses.toLocaleLowerCase()) == true
    );
  }

  $: {
    kereses;
    seachedAugments = augmentkereses();
  }
</script>

<svelte:head>
  <title>TFT Guides to help you get better at the game -WinTFT</title>
  <meta
    name="description"
    content="TFT guides of the highest quality. If you want to know more about a specific comp or get general suggestions on how to improve, we've got you covered. - Patch 12.20b, Set 7.5"
  />
</svelte:head>

<PageLayout>
  <div slot="middle">
    <div class="page">
      <div class="blogContainer">
        <a href="guides/kaisa-reroll" rel="external" class="iDontKnow">
          <div
            class="newestBlog"
            style="background: linear-gradient(rgba(0,0,0,.3), rgba(0,0,0,0.3)), url('/blogBackground/kaisa2.webp') top/cover"
          >
            <div class="topSection">
              <div>
                <p>Newest</p>
              </div>
              <div>
                <p>October 26, 2022</p>
              </div>
            </div>
            <div class="newTitle">
              <p>Kai'Sa Reroll Guide</p>
            </div>
          </div>
        </a>
        <div class="highlightedContainer">
          <div
            class="highlighted"
            style="background: url('/blogBackground/bg3.png') center/cover"
          >
            <a href="guides/level-and-economy-guide" rel="external">
              <div class="highlightedContent">
                <div class="highlightedUp">
                  <p title="Recommended" class="starContainer">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="24"
                      height="24"
                      fill="white"
                      ><path
                        d="m3.1 11.3 3.6 3.3-1 4.6c-.1.6.1 1.2.6 1.5.2.2.5.3.8.3.2 0 .4 0 .6-.1 0 0 .1 0 .1-.1l4.1-2.3 4.1 2.3s.1 0 .1.1c.5.2 1.1.2 1.5-.1.5-.3.7-.9.6-1.5l-1-4.6c.4-.3 1-.9 1.6-1.5l1.9-1.7.1-.1c.4-.4.5-1 .3-1.5s-.6-.9-1.2-1h-.1l-4.7-.5-1.9-4.3s0-.1-.1-.1c-.1-.7-.6-1-1.1-1-.5 0-1 .3-1.3.8 0 0 0 .1-.1.1L8.7 8.2 4 8.7h-.1c-.5.1-1 .5-1.2 1-.1.6 0 1.2.4 1.6z"
                      /></svg
                    >
                  </p>
                  <p>October 24, 2022</p>
                </div>
                <div style="position: relative;">
                  <p class="highlightedText">Level and Economy Guide</p>
                </div>
              </div>
            </a>
          </div>

          <div
            class="highlighted"
            style="background: url('/blogBackground/bg2.png') top/cover"
          >
            <a href="guides/5-tips-to-improve" rel="external">
              <div class="highlightedContent">
                <div class="highlightedUp">
                  <p title="Recommended" class="starContainer">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="24"
                      height="24"
                      version="1.2"
                      fill="white"
                      ><path
                        d="m3.1 11.3 3.6 3.3-1 4.6c-.1.6.1 1.2.6 1.5.2.2.5.3.8.3.2 0 .4 0 .6-.1 0 0 .1 0 .1-.1l4.1-2.3 4.1 2.3s.1 0 .1.1c.5.2 1.1.2 1.5-.1.5-.3.7-.9.6-1.5l-1-4.6c.4-.3 1-.9 1.6-1.5l1.9-1.7.1-.1c.4-.4.5-1 .3-1.5s-.6-.9-1.2-1h-.1l-4.7-.5-1.9-4.3s0-.1-.1-.1c-.1-.7-.6-1-1.1-1-.5 0-1 .3-1.3.8 0 0 0 .1-.1.1L8.7 8.2 4 8.7h-.1c-.5.1-1 .5-1.2 1-.1.6 0 1.2.4 1.6z"
                      /></svg
                    >
                  </p>
                  <p>October 20, 2022</p>
                </div>
                <div style="position: relative;">
                  <p
                    style="position: absolute; bottom: 0; left: 0;"
                    class="highlightedText"
                  >
                    5 Tips To Improve In TFT
                  </p>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
      <div class="searchContainer">
        <div class="searchBox">
          <div class="input-icons">
            <svg
              class="icon"
              xmlns="http://www.w3.org/2000/svg"
              fill="#757575"
              height="25"
              width="25"
              viewBox="0 0 24 24"
            >
              <g data-name="Layer 2">
                <path
                  d="m20.71 19.29-3.4-3.39A7.92 7.92 0 0 0 19 11a8 8 0 1 0-8 8 7.92 7.92 0 0 0 4.9-1.69l3.39 3.4a1 1 0 0 0 1.42 0 1 1 0 0 0 0-1.42zM5 11a6 6 0 1 1 6 6 6 6 0 0 1-6-6z"
                  data-name="search"
                />
              </g>
            </svg>
            <input
              type="text"
              class="input-field"
              placeholder="Search"
              bind:value={kereses}
            />
          </div>
        </div>
      </div>
      <div class="otherBlogs">
        {#each seachedAugments as augment}
          <BlogItem
            bg={augment.bg}
            title={augment.title}
            link={augment.url}
            date={augment.date}
          />
        {/each}
      </div>
    </div>
  </div>
</PageLayout>

<style>
  .iDontKnow {
    width: 65%;
  }
  .highlightedUp {
    display: flex;
    justify-content: space-between;
  }
  .highlightedText {
    position: absolute;
    bottom: 0;
    left: 0;
    font-size: 20px;
  }
  .page {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .highlightedContent {
    height: 95%;
    padding: 5px 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .highlightedContent div {
    height: 100%;
  }

  .otherBlogs {
    max-width: 1005px;
    display: flex;
    gap: 18px;
    align-items: center;
    flex-wrap: wrap;
    margin-bottom: 80px;
  }

  P {
    margin: 0;
    padding: 0;
    color: white;
  }
  .topSection {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    color: white;
    font-size: 22px;
  }
  .newTitle {
    color: white;
    font-size: 26px;
    padding: 20px;
    padding-bottom: 10px;
  }

  .blogContainer {
    margin-top: 120px;
    width: 980px;
    height: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .newestBlog {
    cursor: pointer;
    height: 400px;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .highlightedContainer {
    margin-left: 16px;
    width: 35%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .highlighted {
    cursor: pointer;
    width: 100%;
    height: 192px;
  }

  .searchContainer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 980px;
    min-width: 980px;
    margin: 0 auto;
    margin-bottom: 18px;
    margin-top: 50px;
  }

  .highlighted:nth-child(1) {
    margin-bottom: 17px;
  }

  .searchBox div input {
    min-width: 225px;
    padding-top: 3px;
    font-size: 16px;
    font-weight: 600;
    padding-left: 8px;
    height: 32px;
    background-color: #2d2f3a;
    border: 1px solid #5e5d5d;
    outline: none;
  }

  .input-icons svg {
    position: absolute;
    height: 30px;
    padding: 0;
  }

  .input-icons {
    width: 100%;
    position: relative;
  }

  .icon {
    padding: 10px;
    left: 202px;
    top: 5px;
  }

  .input-field {
    color: white;
    font-weight: 400;
  }

  @media (max-width: 1400px) {
    .iDontKnow {
      width: auto;
    }

    .blogContainer {
      flex-direction: column;
      height: 600px;
      width: 800px;
      align-items: center;
      justify-content: start;
      gap: 18px;
    }

    .highlightedContainer {
      flex-direction: row;
      width: 700px;
      margin: 0;
      gap: 18px;
    }

    .newestBlog {
      width: 700px;
    }
    .page {
      max-width: 700px;
    }
    .searchContainer {
      min-width: 700px;
      max-width: none;
    }

    @media (max-width: 820px) {
      .newestBlog {
        width: 360px;
        height: 200px;
      }
      .newestBlog p {
        font-size: 18px;
      }
      .newestBlog div {
        padding: 6px;
      }
      .highlightedContainer {
        width: 360px;
        flex-direction: column;
        max-height: 220px;
      }
      .highlighted {
        height: 100px;
      }

      .highlighted:nth-child(1) {
        margin-bottom: 0px;
        display: none;
      }

      .highlightedContent p {
        font-size: 18px;
        margin-bottom: 4px;
      }

      .highlightedUp p {
        font-size: 16px;
      }
      .starContainer {
        display: block;
      }
      .searchContainer {
        margin-top: 40px;
        margin-bottom: 20px;
        min-width: 360px;
        max-width: none;
        justify-content: center;
      }
      .page {
        max-width: 360px;
      }
      .otherBlogs {
        justify-content: center;
      }
      .blogContainer {
        margin-top: 90px;
        height: 330px;
        width: 360px;
      }
      .searchBox div input {
        width: 348px;
      }
      .icon {
        padding: 10px;
        left: 328px;
        top: 5px;
      }
    }
  }
</style>
