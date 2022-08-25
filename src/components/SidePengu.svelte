<style>
    div{
        color: white;
    }
    .textBox{
        border: 1px solid #5e5d5d;
        position: relative;
        height: 140px;
        width: 270px;
        background-color: #22242f;
    }
</style>

<div style="padding-top: 120px;">
    <div class="textBox">
        <img style="position: absolute; left: 120px; top: -70px;" src="pengu.webp" alt="">
        <div style="padding: 15px; padding-right: 60px;">
            <slot></slot>
        </div>
    </div>
</div>