<script>
  import Champ from "./Champ.svelte";
  import { onMount } from "svelte";
  import TraitDetails from "./TraitDetails.svelte";
  export let itemData;

  export let AllChampions;

  export let id;
  export let name;
  export let tier;
  export let positions;
  export let carries;
  export let difficulty;
  export let type;
  export let carousel;
  export let augments;
  export let lvl9;
  export let guide = "";
  let hasGude = false;
  if (guide != "") {
    hasGude = true;
  }
  export let threeStar;
  export let optionsChampionsRight;
  export let optionsChampionsLeft;

  let dColor;
  let bdColor;

  let tColor;
  let btColor;

  function getChampDetails(champName) {
    let res = AllChampions.find((obj) => {
      if (obj.Name == champName) {
        return obj;
      }
    });
    return res;
  }

  export let tiercolor;

  dColor = "#FD5C62";
  bdColor = "#5E0B0D";

  tColor = "#F8A2FC";
  btColor = "#6D3D74";

  if (difficulty == "Easy") {
    dColor = "#23F5C1";
    bdColor = "#0E6952";
  } else if (difficulty == "Medium") {
    dColor = "#FFA366";
    bdColor = "#664227";
  }

  if (type == "Standard") {
    tColor = "#7BA7FF";
    btColor = "#203980";
  } else if (type == "Fast 8") {
    tColor = "#EECAD5";
    btColor = "#73535C";
  } else if (type == "Hyper Roll") {
    tColor = "#FFF38B";
    btColor = "#7A6D44";
  }
  export let champions;

  let growid = "grow" + id;

  let rotate = false;
  function clickonArrow() {
    rotate = !rotate;
    growDivv();
  }

  function growDivv() {
    let growDiv = document.querySelector("." + growid);
    if (growDiv.clientHeight) {
      growDiv.style.height = 0;
      growDiv.style.borderBottom = 0;
    } else {
      if (growDiv.clientWidth < 400) {
        growDiv.style.height = 470 + "px";
      } else {
        growDiv.style.height = 230 + "px";
      }
      growDiv.style.border = "1px solid #5e5d5d";

      growDiv.style.borderTop = 0;
    }
  }

  function getName(namex) {
    namex = namex.replaceAll(" ", "");
    namex = namex.toLowerCase();
    return namex;
  }

  export let Gtraits;
  export let Straits;
  export let Btraits;

  export let augmentData;

  function determineValue(champ) {
    var result = AllChampions.find((obj) => {
      return obj.Name == champ;
    });
    return result.Cost;
  }

  function isThreeStar(champ) {
    if (threeStar.find((element) => element == champ)) {
      return true;
    } else {
      return false;
    }
  }

  let augNames = [];
  let l = 0;

  augments.forEach((element) => {
    augmentData.find((x) => {
      if (x.src == element) {
        augNames[l] = x.name;
        l++;
      }
    });
  });

  l = -1;
  function augNamesf() {
    l++;
    return augNames[l];
  }

  function traitChange(t) {
    t = t.replaceAll(" ", "");
    if (t == "Underground") {
      return "theunderground";
    } else if (t == "Mecha:PRIME" || t == "mecha:prime") {
      return "mechaprime";
    } else {
      t = t.toLowerCase();
      return t;
    }
  }

  function findTrait(nm) {
    for (let i = 0; i < traitData.length; i++) {
      if (traitData[i].Name == nm) {
        return traitData[i];
      }
    }
  }
</script>

<div class="mainCompContainer">
  <div class="compHead">
    <p>{name}</p>
    <div class="guidePic" class:hasGude={!hasGude}>
      <a href={guide} style="display: flex; align-items:center;" rel="external">
        <img src="guidePic.png" alt="linktoguide" height="20" />
      </a>
    </div>
  </div>
  <div class="compBody">
    <div class="compInfo">
      <div class="SLetter" style="background-color: #{tiercolor};">
        {tier}
      </div>
      <div class="compStat">
        <div class="difficulty" style="background-color: {bdColor};">
          <p style="color: {dColor};">{difficulty}</p>
        </div>
        <div class="type" style="background-color: {btColor};">
          <p style="color: {tColor};">{type}</p>
        </div>
      </div>
      <div class="arrowa" on:click={clickonArrow} class:fordul={rotate}>
        <svg
          stroke="currentColor"
          fill="currentColor"
          stroke-width="0"
          viewBox="0 0 24 24"
          height="35px"
          width="35px"
          xmlns="http://www.w3.org/2000/svg"
          ><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" /></svg
        >
      </div>
    </div>
    <div class="compBodyRight">
      <div class="champs">
        {#each champions as champ}
          {#if champ == carries[0].name}
            <Champ
              AllChampions={getChampDetails(champ)}
              {itemData}
              actualNamename={champ}
              name={getName(champ)}
              Items={carries[0].items}
              cost={determineValue(champ)}
              ThreeStar={isThreeStar(champ)}
            />
          {:else if champ == carries[1].name}
            <Champ
              AllChampions={getChampDetails(champ)}
              actualNamename={champ}
              {itemData}
              name={getName(champ)}
              Items={carries[1].items}
              cost={determineValue(champ)}
              ThreeStar={isThreeStar(champ)}
            />
          {:else if champ == carries[2].name}
            <Champ
              actualNamename={champ}
              AllChampions={getChampDetails(champ)}
              {itemData}
              name={getName(champ)}
              Items={carries[2].items}
              cost={determineValue(champ)}
              ThreeStar={isThreeStar(champ)}
            />
          {:else}
            <Champ
              actualNamename={champ}
              AllChampions={getChampDetails(champ)}
              {itemData}
              name={getName(champ)}
              cost={determineValue(champ)}
              ThreeStar={isThreeStar(champ)}
            />
          {/if}
        {/each}
      </div>
      <div class="arrow" on:click={clickonArrow} class:fordul={rotate}>
        <svg
          stroke="currentColor"
          fill="currentColor"
          stroke-width="0"
          viewBox="0 0 24 24"
          height="35px"
          width="35px"
          xmlns="http://www.w3.org/2000/svg"
          ><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" /></svg
        >
      </div>
    </div>
  </div>
  <div class="compExpanded grow {growid}">
    <div class="compExpandedLeft">
      <div class="LeftUp">
        <p
          style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;"
        >
          Augments
        </p>
        <div class="augmentContainer">
          {#each augments as augment}
            <img
              src="./augments/{augment}.png"
              alt={augment}
              loading="lazy"
              decoding="async"
              title={augNamesf()}
            />
          {/each}
        </div>
      </div>
      <div class="LeftDown">
        <p
          style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;"
        >
          Options
        </p>
        <div class="optionsContainer">
          <div class="option1">
            <div class="lvl9">Lvl 9</div>
            <Champ
              actualNamename="0"
              AllChampions={getChampDetails(lvl9)}
              {itemData}
              name={getName(lvl9)}
              augment={true}
              cost={determineValue(lvl9)}
            />
          </div>
          <div class="option2">
            <div class="option2Left">
              {#each optionsChampionsLeft as ocl}
                <Champ
                  actualNamename="0"
                  AllChampions={getChampDetails(ocl)}
                  {itemData}
                  name={getName(ocl)}
                  augment={true}
                  cost={determineValue(ocl)}
                />
              {/each}
            </div>
            <div class="arrow">
              <svg
                stroke="currentColor"
                fill="currentColor"
                stroke-width="0"
                viewBox="0 0 24 24"
                height="35px"
                width="35px"
                xmlns="http://www.w3.org/2000/svg"
                ><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" /></svg
              >
            </div>
            <div class="option2Right">
              {#each optionsChampionsRight as ocr}
                <Champ
                  actualNamename="0"
                  AllChampions={getChampDetails(ocr)}
                  {itemData}
                  name={getName(ocr)}
                  augment={true}
                  cost={determineValue(ocr)}
                />
              {/each}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="compExpandedLeft">
      <div class="MiddleUp">
        <p
          class=""
          style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;"
        >
          Traits
        </p>
        <div
          style="display: flex; justify-content: center; align-items: center; height: 65%;"
        >
          <div>
            <div class="traitContainer">
              {#each Gtraits as trait}
                <div class="traitItem" style="background-color: #d5ac38;">
                  <img
                    src="./Traits/{traitChange(
                      trait.substring(0, trait.length - 1)
                    )}.webp"
                    alt={trait.substring(0, trait.length - 1)}
                    title="{trait.slice(-1)} {trait.substring(
                      0,
                      trait.length - 1
                    )}"
                    height="24px"
                    width="24px"
                    loading="lazy"
                    decoding="async"
                  />
                </div>
              {/each}
              {#each Straits as trait}
                <div class="traitItem" style="background-color: #8a9c9d">
                  <img
                    src="./Traits/{traitChange(
                      trait.substring(0, trait.length - 1)
                    )}.webp"
                    alt={trait.substring(0, trait.length - 1)}
                    title="{trait.slice(-1)} {trait.substring(
                      0,
                      trait.length - 1
                    )}"
                    height="24px"
                    width="24px"
                    loading="lazy"
                    decoding="async"
                  />
                </div>
              {/each}
              {#each Btraits as trait}
                <div class="traitItem" style="background-color: #966b51">
                  <img
                    src="./Traits/{traitChange(
                      trait.substring(0, trait.length - 1)
                    )}.webp"
                    alt={trait.substring(0, trait.length - 1)}
                    title="{trait.slice(-1)} {trait.substring(
                      0,
                      trait.length - 1
                    )}"
                    height="24px"
                    width="24px"
                    loading="lazy"
                    decoding="async"
                  />
                </div>
              {/each}
            </div>
          </div>
        </div>
      </div>
      <div class="MiddleDown">
        <p
          class=""
          style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;"
        >
          Carousel
        </p>
        <div class="carouselContainer">
          <img
            src="./items/{carousel[0]}.webp"
            alt={carousel[0]}
            loading="lazy"
            decoding="async"
          />
          <svg
            stroke="currentColor"
            fill="currentColor"
            stroke-width="0"
            viewBox="0 0 24 24"
            height="35px"
            width="35px"
            xmlns="http://www.w3.org/2000/svg"
            ><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" /></svg
          >
          <img
            src="./items/{carousel[1]}.webp"
            alt={carousel[1]}
            loading="lazy"
            decoding="async"
          />
          <svg
            stroke="currentColor"
            fill="currentColor"
            stroke-width="0"
            viewBox="0 0 24 24"
            height="35px"
            width="35px"
            xmlns="http://www.w3.org/2000/svg"
            ><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z" /></svg
          >
          <img
            src="./items/{carousel[2]}.webp"
            alt={carousel[2]}
            loading="lazy"
            decoding="async"
          />
        </div>
      </div>
    </div>
    <div class="compExpandedRight">
      <p
        class=""
        style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px; margin-bottom: 20px;"
      >
        Positioning
      </p>
      <div class="mainx">
        <div class="positionContainer">
          {#each positions as position}
            <div>
              {#if position != ""}
                <img
                  src="./ChampIcons/tft8_{position}.webp"
                  alt={position}
                  title={position}
                  loading="lazy"
                  decoding="async"
                />
              {/if}
            </div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .hasGude {
    display: none;
  }

  .guidePic {
    position: absolute;
    right: 0;
  }

  p {
    margin: 0;
    padding: 0;
  }

  .mainCompContainer {
    width: 980px;
    margin-bottom: 20px;
  }

  .compHead {
    background-color: #2d2f3a;
    height: 26px;
    color: white;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid #5e5d5d;
    border-bottom: 0;
    position: relative;
  }

  .compBody {
    height: 100px;
    background-color: #22242f;
    border: 1px solid #5e5d5d;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 35px;
  }

  .compInfo {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .SLetter {
    height: 40px;
    width: 40px;
    background-color: #f05867;
    border-radius: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    color: black;
    margin-right: 35px;
  }

  .compStat {
    width: 125px;
    line-height: 12px;
    color: white;
  }

  .compBodyRight {
    display: flex;
    justify-content: end;
    align-items: center;
  }

  .champs {
    display: flex;
    flex-direction: row-reverse;
    justify-content: end;
    flex-wrap: wrap-reverse;
    align-items: center;
    margin-right: 35px;
    gap: 15px;
  }

  .arrow {
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    user-select: none;
  }
  .arrow svg {
    cursor: pointer;
  }

  .arrowa {
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    user-select: none;
    display: none;
  }

  .arrowa svg {
    cursor: pointer;
  }

  .fordul {
    transform: rotate(180deg);
    -ms-transform: rotate(180deg);
    -webkit-transform: rotate(180deg);
  }

  .difficulty {
    color: #2cffca;
    background-color: #25655e;
    height: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0px 32px;
    margin-bottom: 3px;
    padding: 0px 34px;
    font-size: 14px;
    font-weight: 600;
  }

  .type {
    color: #eedc82;
    background-color: #5f5b48;
    height: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 6px;
    font-size: 14px;
    font-weight: 600;
  }
  .compExpanded {
    height: 600px;
    background-color: #22242f;
    border: 1px solid #5e5d5d;
    display: flex;
    align-items: center;
    justify-content: center;
    border-top: 0;
    border-bottom: 0;
    text-align: center;
  }

  .compExpandedRight {
    height: 100%;
    width: 100%;
  }

  .compExpandedMiddle {
    border-right: 1px solid #5e5d5d;
    height: 100%;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .MiddleUp {
    border-bottom: 1px solid #5e5d5d;
    min-height: 140px;
    width: 100%;
  }

  .MiddleDown {
    min-height: 91px;
    width: 100%;
  }

  .carouselContainer {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .carouselContainer svg {
    rotate: -90deg;
    color: white;
  }

  .carouselContainer img {
    height: 37px;
    width: 37px;
  }

  .compExpandedLeft {
    border-right: 1px solid #5e5d5d;
    height: 100%;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .LeftUp {
    width: 100%;
    min-height: 93px;
    border-bottom: 1px solid #5e5d5d;
  }

  .LeftDown {
    width: 100%;
    min-height: 40%;
  }

  .augmentContainer {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .augmentContainer img {
    height: 50px;
  }

  .optionsContainer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }

  .option1 {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }

  .option1 svg {
    rotate: 90deg;
  }

  .option2 svg {
    rotate: 90deg;
  }

  .option2 {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .traitContainer {
    padding: 0 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 4px;
    margin-bottom: 4px;
  }

  .traitContainer div {
    height: 24px;
    padding: 4px 0;
    width: 42px;
    background-color: #2d2f3a;
    color: white;
    border-radius: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .mainx {
    display: flex;
    --s: 34px;
    --m: 2px;
    --f: calc(1.732 * var(--s) + 4 * var(--m) - 1px);
  }

  .positionContainer {
    font-size: 0;
    margin: 0;
    padding: 20px;
    padding-top: 0px;
    line-height: normal;
    text-align: left;
  }

  .positionContainer div {
    margin: 0;
    padding: 0;
    position: relative;
    width: var(--s);
    margin: var(--m);
    height: calc(var(--s) * 1.1547);
    display: inline-block;
    font-size: initial;
    clip-path: polygon(0% 25%, 0% 75%, 50% 100%, 100% 75%, 100% 25%, 50% 0%);
    background: #3d4155;
    margin-bottom: calc(var(--m) - var(--s) * 0.2885);
  }
  .positionContainer::before {
    content: "";
    width: calc(var(--s) / 2 + var(--m));
    float: left;
    height: 120%;
    shape-outside: repeating-linear-gradient(
      #0000 0 calc(var(--f) - 3px),
      #000 0 var(--f)
    );
  }

  .grow {
    -moz-transition: height 0.4s;
    -ms-transition: height 0.4s;
    -o-transition: height 0.4s;
    -webkit-transition: height 0.4s;
    transition: height 0.4s;
    height: 0;
    overflow: hidden;
  }

  .traitItem {
    height: 50px;
    width: 50px;
  }

  .positionContainer div img {
    position: absolute;
    height: 40px;
    transform: scale(1);
  }

  .lvl9 {
    border-radius: 2px;
    background-color: #323441;
    color: white;
    padding: 3px 10px;
  }

  .option2Right,
  .option2Left {
    display: flex;
    align-items: baseline;
    justify-content: center;
    gap: 5px;
  }

  @media (max-width: 1100px) {
    .champs {
      width: 290px;
      row-gap: 24px;
    }

    .compBody {
      height: 190px;
    }

    .mainCompContainer {
      width: 600px;
      margin-right: 0;
    }

    .compInfo {
      flex-direction: column;
      align-items: center;
      justify-content: center;
      row-gap: 30px;
      margin-left: 8px;
    }

    .SLetter {
      margin: 0;
    }

    .compExpandedRight {
      display: none;
    }

    .compExpandedLeft:nth-child(2) {
      border: 0;
    }
  }

  @media (max-width: 720px) {
    .compInfo {
      margin: 0;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      gap: 32px;
    }
    .SLetter {
      margin: 0;
    }
    .compBody {
      flex-direction: column;
      justify-content: center;
      gap: 30px;
    }

    .compStat {
      margin-right: 1px;
    }

    .compBody {
      height: 280px;
    }

    .arrow {
      display: none;
    }

    .champs {
      margin: 0;
      width: 286px;
    }
    .arrowa {
      display: block;
      margin-left: 4px;
    }
    .mainCompContainer {
      width: 346px;
      margin-right: 0;
    }

    .compExpandedRight {
      display: none;
    }

    .compExpanded {
      flex-direction: column-reverse;
    }

    .MiddleUp {
      height: 100%;
    }
    .compExpandedLeft {
      height: auto;
      border-right: 0;
    }

    .LeftUp {
      border-top: 1px solid #5e5d5d;
    }

    .traitContainer {
      padding: 0 20px;
    }

    .option2 .arrow {
      height: 25px;
      width: 25px;
      margin-right: 11px;
      padding-bottom: 10px;
      display: block;
    }
  }
</style>
