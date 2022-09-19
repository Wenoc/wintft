<script>
    export let headerText;
    export let description = false;
    export let text = "TFTea helps you with Team Composition guides, so that you'll always be able to start your games one step ahead of your opponents."
    if(description == false){
        text = '';
    }
</script>

<style>
    .up{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .mainText{
        color: white;
        font-size: 40px;
        line-height: 30px;
        max-width: 300px;
    }
    svg#chart {
        background: #b97331;
        width: 3px;
    }
    .down p{
        color: gray;
        text-align: center;
        max-width: 630px;
        margin-top: 0;
        font-weight: 500;
    }
    .brandtext{
        margin-right: 28px;
        width: 240px;
        height: 70px;
    }
    @media(max-width:1200px){
        .brandtext{
            margin-right: 0;
        }
        .up div:nth-child(2){
            display: none;
        }
        .up div:nth-child(3){
            display: none;
        }
    }
    @media(max-width:776px){
        .down {
            max-width: 75%;
        }
        .brandtext{
            width: 200px;
            height: 30px;
            margin-bottom: 40px;
        }
    }

    p{
        margin: 0;
        padding-bottom: 6px;
    }
</style>

<div style="margin-top: 134px; margin-bottom: 50px; display: flex; flex-direction: column; align-items: center;">
    <div class="up">
        <div class="brandtext" style="text-align: right;">
            <img src="brand.svg" alt="brand logo" style="width: 85%;">
        </div>
        <div style="padding-top: 5px;" class="svgContainer">
            <svg id="chart" width="1" height="50">
                <line x1="20" y1="20" x2="20" y2="130"></line>
            </svg>
        </div>
        <div style="margin-left: 28px;">
            <p class="mainText" style="width: 260px; text-align: start;">{headerText}</p>
        </div>
    </div>
    <div class="down">
        <p>{text}</p>
    </div>
</div>
