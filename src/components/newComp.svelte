<script>
    import Champ from "./Champ.svelte";
    export let ChamionCost;
    export let id;

    let growid = 'grow' + id;

    let rotate = false
    function clickonArrow(){
        rotate = !rotate
        growDivv();
    }
    
    function growDivv(){
        let growDiv = document.querySelector('.'+growid);
        if (growDiv.clientHeight) {
        growDiv.style.height = 0;
        growDiv.style.borderBottom = 0;
    } else {
        growDiv.style.height = 300 + "px";
        growDiv.style.border = '1px solid #5e5d5d'
        growDiv.style.borderLeft = 0;
        growDiv.style.borderTop = 0;
    }
    }

    let traits = [1, 2, 3, 4, 5, 6];

</script>

<style>
    p{
        margin: 0;
        padding: 0;
    }
    .compHead{
        background-color: #2d2f3a;
        height: 30px;
        color: white;
        font-weight: 600;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid #5e5d5d;
        border-bottom: 0;
    }

    .compBody{
        height: 100px;
        background-color: #22242f;
        border: 1px solid #5e5d5d;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 35px;
    }

    .compInfo{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .SLetter{
        height: 42px;
        width: 42px;
        background-color: #f05867;
        border-radius: 3px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        color: black;
        margin-right: 35px;
    }

    .compStat{
        line-height: 12px;
        color: white;
    }

    .compBodyRight{
        display: flex;
        justify-content: end;
        align-items: center;
    }

    .champs{
        display: flex;
        flex-direction: row-reverse;
        justify-content: end;
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

    .fordul {
        transform:rotate(180deg);
        -ms-transform:rotate(180deg);
        -webkit-transform:rotate(180deg);
    }

    .difficulty{
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

    .type{
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
    .compExpanded{
        height: 230px;
        background-color: #22242f;
        border: 1px solid #5e5d5d;
        display: flex;
        align-items: center;
        justify-content: center;
        border-top: 0;
    }

    .compExpandedRight{
        height: 100%;
        width: 100%;
    }

    .compExpandedMiddle{
        border-right: 1px solid #5e5d5d;
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }

    .MiddleUp{
        border-bottom: 1px solid #5e5d5d;
        min-height: 60%;
        width: 100%;
    }

    .MiddleDown{
        min-height: 40%;
        width: 100%;
    }

    .carouselContainer{
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .carouselContainer svg{
        rotate: -90deg;
        color: white;
    }

    .carouselContainer img{
        height: 37px;
        width: 37px;
    }

    .compExpandedLeft{
        border-right: 1px solid #5e5d5d;
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .LeftUp{
        width: 100%;
        min-height: 40%;
        border-bottom: 1px solid #5e5d5d;
    }

    .LeftDown{
        width: 100%;
    }

    .augmentContainer{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .augmentContainer img{
        height: 50px;
    }

    .optionsContainer{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 10px;
    }
    
    .option1{
        display: flex;
        justify-content: center;
        align-items: center;
    }


    .option1 svg{
        rotate: 90deg;
    }

    .option2 svg{
        rotate: 90deg;
    }

    .option2{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .traitContainer{
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 4px;
        margin-bottom: 4px;
    }

    .traitContainer div{
        height: 32px;
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

    .positionContainer{
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
        height: calc(var(--s)*1.1547);
        display: inline-block;
        font-size: initial;
        clip-path: polygon(0% 25%, 0% 75%, 50% 100%, 100% 75%, 100% 25%, 50% 0%);
        background: #525461;
        margin-bottom: calc(var(--m) - var(--s)*0.2885);
    }
    .positionContainer::before {
        content: "";
        width: calc(var(--s)/2 + var(--m));
        float: left;
        height: 120%;
        shape-outside: repeating-linear-gradient(#0000 0 calc(var(--f) - 3px),
            #000 0 var(--f));
    }

    .positionContainer div img {
        position: absolute;
        top: 9px;
        left: 5px;
        height: 40px;
        transform: scale(1.6);
    }
</style>

<div style="margin-bottom: 20px; width: 980px;">
    <div class="compHead">
        <!-- nevet valtoztatni -->
        <p>4 Whisperers 2 Trainers</p>
    </div>
    <div class="compBody">
        <div class="compInfo">
            <div class="SLetter">
                S
            </div>
            <div class="compStat">
                <div class="difficulty">
                    <p>Easy</p>
                </div>
                <div class="type">
                    <p>Hyper Roll</p>
                </div>
            </div>
        </div>
        <div class="compBodyRight">
            <div class="champs">
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
                <Champ {ChamionCost}/>
            </div>
            <div class="arrow" on:click={clickonArrow} class:fordul={rotate}>
                <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
            </div>
        </div>
    </div>
    <div class="compExpanded">
        <div class="compExpandedLeft">
            <div class="LeftUp">
                <p class="" style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;">Augments</p>
                <div class="augmentContainer">
                    <img src="./augments/dragonbane-crown-iii.png" alt="">
                    <img src="./augments/dragonbane-crown-iii.png" alt="">
                    <img src="./augments/dragonbane-crown-iii.png" alt="">
                </div>
            </div>
            <div class="LeftDown">
                <p class="" style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;">Options</p>
                <div class="optionsContainer">
                    <div class="option1">
                        <Champ {ChamionCost} Items={[]} augment={true}/>
                        <!-- more -->
                        <div class="arrow">
                            <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                        </div>
                        <Champ {ChamionCost} Items={[]} augment={true}/>
                        <!-- more -->
                    </div>
                    <div class="option2">
                        <Champ {ChamionCost} Items={[]} augment={true}/>
                        <!-- more -->

                        <div class="arrow">
                            <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                        </div>
                        <Champ {ChamionCost} Items={[]} augment={true}/>
                        <!-- more -->
                    </div>
                </div>
            </div>
        </div>
        <div class="compExpandedMiddle">
            <div class="MiddleUp">
                <p class="" style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;">Traits</p>
                <div style="display: flex; justify-content: center; align-items: center; height: 65%;">
                    <div>
                        <div class="traitContainer">
                            {#each traits as trait}
                                <div>{trait}</div>
                            {/each}
                        </div>
                        <div class="traitContainer">
                            <div>1</div>
                            <div>2</div>
                            <div>3</div>
                            <div>4</div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="MiddleDown">
                <p class="" style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px;">Carousel</p>
                <div class="carouselContainer">
                    <img src="./items/Bloodthirster.png" alt="">
                    <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                    <img src="./items/Bloodthirster.png" alt="">
                    <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                    <img src="./items/Bloodthirster.png" alt="">
                </div>
            </div>
        </div>
        <div class="compExpandedRight">
            <p class="" style="color: white; padding-top: 8px; padding-bottom: 4px; font-size: 14px; margin-bottom: 20px;">Positioning</p>
            <div class="mainx">
                <div class="positionContainer">
                    <div></div>
                    <div></div>
                    <div></div>
                    <div><img src="./img/Syfen.png" alt=""></div>
                    <div><img src="./img/Sylas.png" alt=""></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div><img src="./img/TrainderDragon.webp" alt=""></div>
                    <div><img src="./img/Sona.png" alt=""></div>
                    <div><img src="./img/Tristana.png" alt=""></div>
                    <div></div>
                    <div><img src="./img/Bard.png" alt=""></div>
                    <div></div>
                    <div><img src="./img/Lulu.png" alt=""></div>
                    <div><img src="./img/Corki.png" alt=""></div>
                </div>
            </div>
        </div>
    </div>
</div>