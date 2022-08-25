<script>
    import Champ from "./Champ.svelte";
    export let ChamionCost;
</script>

<style>
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
        padding: 0 30px;
    }

    .compInfo{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .SLetter{
        height: 45px;
        width: 45px;
        background-color: #f05867;
        border-radius: 3px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        color: black;
        margin-right: 26px;
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
        margin-right: 30px;
        gap: 15px;
    }

    .arrow {
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
    }
    .arrow svg {
        cursor: pointer;
    }

    .compExpanded{
        height: 300px;
        background-color: #22242f;
        border: 1px solid #5e5d5d;
        border-top: 0;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .compExpandedLeft{
        border-right: 1px solid #5e5d5d;
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .compExpandedRight{
        width: 100%;
        height: 100%;
        text-align: center;
    }

    .up{
        width: 100%;
        height: 100%;
        border-bottom: 1px solid #5e5d5d;
        text-align: center;
    }

    .down{
        text-align: center;
        width: 100%;
        height: 100%;
    }

    .mainx {
        display: flex;
        --s: 50px;
        --m: 3px;
        --f: calc(1.732 * var(--s) + 4 * var(--m) - 1px);
    }

    .positionContainer{
        font-size: 0;
        margin: 0;
        padding: 20px;
        padding-top: 0px;
        padding-left: 33px;
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

    #traits .mainx .positionContainer div img {
        position: absolute;
        top: 9px;
        left: 5px;
        height: 40px;
        transform: scale(1);
    }
    .CarouselPrio{
        margin-top: 30px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .CarouselPrio img{
        width: 45px;
    }
    .CarouselPrio svg{
        rotate: -90deg;
        color: white;
    }


    @media(max-width:1200px){
        .compBody{
            padding-top: 10px;
            flex-direction: column;
            justify-content: unset;
            height: 180px;
            gap: 10px;
        }
        .compExpanded{
            display: none;
        }
        .arrow{
            display: none;
        }
        .champs{
            margin-right: 0;
            zoom: 0.85; 
            -moz-transform: scale(0.85); 
        }
        .compBodyRight{
            padding: 0 auto;
        }
	}
    @media(max-width:776px){
        .champs{
            margin-right: 0;
            zoom: 0.75; 
            -moz-transform: scale(0.75); 
        }
        .compBody{
            padding-top: 10px;
            flex-direction: column;
            justify-content: unset;
            height: 160px;
        }
    }

    @media(max-width:580px){
        .champs{
            width: 288px;
            flex-wrap: wrap;
            align-items: center;
            height: 170px;
        }
        .compBody{
            height: 230px;
            gap: 0px;
        }
    }
</style>

<div>
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
                <!-- megvaltoztni ezeket -->
                <p>Avg Place: <span>3.81</span></p>
                <p>Pick Rate: <span>0.81</span></p>
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
            <div class="arrow">
                <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
            </div>
        </div>
    </div>
    <div class="compExpanded">
        <div class="compExpandedLeft">
            <div class="up">
                <p style="color: white; font-weight: 400;">Main Traits</p>
                <div id="traits" style="display: flex; justify-content: center;">
                    <div class="mainx" style="margin: 0;">
                        <div class="positionContainer" style="padding: 0; text-align: center;">
                            <div></div>
                            <div></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="down">
                <p style="color: white; font-weight: 400;">Carousel</p>
                <div class="CarouselPrio">
                    <img src="items/Bloodthirster.png" alt="">
                    <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                    <img src="items/Bloodthirster.png" alt="">
                    <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg"><path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path></svg>
                    <img src="items/Bloodthirster.png" alt="">
                </div>
            </div>
        </div>
        <div class="compExpandedRight">
            <p style="color: white; font-weight: 400;">Positioning</p>
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