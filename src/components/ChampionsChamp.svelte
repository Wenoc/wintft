

<script>
    import { onMount } from 'svelte';
    export let items;
    let newItems = [];

    onMount(async () => {
        items.forEach(item => {
        let newItem;
        newItem = item.replaceAll("\'", "");
        newItem = newItem.replaceAll(" ", "");

        newItems.push(newItem);
    });
    items = newItems;
    });

    export let name;
    export let traits;
</script>

<div class="opacity">
    <div class="champCard" style="background: linear-gradient(rgba(0,0,0,.5), rgba(0,0,0,0.5)), url('/ChampThumbnails/{name}.jpg'); background-size: cover;">
        <div class="cardLeft">
            <div class="leftUp">
                <div class="champTraits">
                    {#each traits as trait}
                    <div class="traitItem">
                        <img src="./Traits/Set7_{trait}_w.svg" alt="">
                        <p>{trait}</p>
                    </div>
                    {/each}
                </div>
            </div>
            <div class="leftDown" style="position: relative;">
                <p class="champName" style="padding-left: 6px;">{name}</p>
            </div>
        </div>
        <div class="cardRight">
            <div class="rightUp">
                <div class="champCost">
                    <img src="./augments/dragonbane-crown-iii.png" alt="">
                    <p>1</p>
                </div>
            </div>
            <div class="rightDown">
                <div class="champItems">
                    {#each items as item}
                        <img src="./items/{item}.png" alt="">
                    {/each}
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    p{
        margin: 0;
        padding: 0;
    }

    .champCard{
        border: 1px solid #202020;
        color: white;
        height: 180px;
        width: 300px;
        padding: 5px;
        border-radius: 4px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .cardRight{
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        
    }

    .cardLeft{
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .leftUp{
        height: 100%;
        width: 100%;
    }

    .leftDown{
        height: 100%;
        width: 100%;
    }

    .rightUp{
        position: relative;
        height: 100%;
        width: 100%;
    }

    .rightDown{
        height: 100%;
        width: 100%;
        position: relative;
    }

    .traitItem{
        display: flex;
        justify-content: start;
        align-items: center;
        font-size: 16px;
        font-weight: 600;
    }

    .traitItem img{
        height: 30px;
        margin-right: 6px;
    }

    .champName{
        position: absolute; 
        bottom: 0;
        font-size: 22px;
    }

    .champCost{
        position: absolute;
        right: 0;
        display: flex;
        justify-content: start;
        align-items: center;
        padding-right: 6px;
    }

    .champCost img{
        height: 30px;
    }

    .champItems{
        position: absolute; 
        bottom: 0;
        right: 0;
        padding-right: 4px;
        padding-bottom: 4px;
        display: flex;
        justify-content: start;
        align-items: center;
        gap: 4px;
    }

    .champItems img{
        height: 26px;
    }
</style>