
<script>
    export let Name = 'Aatrox';
    // export let Rarity;
    export let Items = ['Bloodthirster', 'Bloodthirster', 'Bloodthirster'];
    export let ThreeStar = false;
    // export let ChamionCost;
    // let index = ChamionCost.findIndex(x => x.name === Name);
    // let ChampRaity = ChamionCost[index].cost;
    let borderColor ='#878aa2';
    export let augment = false;

    // let borderColor;
    // if (ChampRaity == 1){
    //     borderColor ='#878aa2';
    // } else if(ChampRaity == 2){
    //     borderColor ='#11b88e';
    // } else if(ChampRaity == 3){
    //     borderColor ='#417deb';
    // }else if(ChampRaity == 4 || ChampRaity == 8){
    //     borderColor ='#c92a73';
    // }else if(ChampRaity == 5 || ChampRaity == 10){
    //     borderColor ='#f2c530';
    // }
</script>

<style>
    .augment{
        height: 40px;
        width: 40px;
    }

    .noaugment{
        height: 60px;
        width: 60px;
    }

    .champContainer{
        outline-offset: -3px;
        border-radius: 2px;
    }
    .stars img{
        width: 18px;
    }
    .stars{
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: -10px;
        right: -2px;
    }

    .items img{
        width: 20px;
        border: 1px solid black;
    }

    .items{
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 52px;
        right: -4px;
        gap: 1px;
    }

    .dontShow{
        display: none;
    }

    .items2{
        right: 8px;
    }

    .items3{
        right: 18px;
    }

    
</style>

<div style="position: relative;">
    <div class="champContainer" class:augment={augment} class:noaugment={!augment} style="outline: 3px solid {borderColor};">
        <img src="ChampIcons/syfen.png" alt="" style="max-width:100%;">
    </div>
    <div class="stars" class:dontShow={!ThreeStar}>
        <div style="position: relative;">
            <img src="star.svg" alt="" style="position: absolute; left: -55px;">
            <img src="star.svg" alt="" style="position: absolute; left: -40px;">
            <img src="star.svg" alt="" style="position: absolute; left: -25px;">
        </div>
    </div>
    <div class="items" class:items2={Items.length == 2} class:items3={Items.length == 1}>
        {#each Items as item}
        <img src="items/{item}.png" alt="">
        {/each}
    </div>
</div>