<script>
    export let isSecond = false;
    // export let augment = '';
    // export let tier = '';
    // export let avgPlace = '';
    // export let Descriptio = '';
</script>

<div class="augment" class:second={isSecond}>
    <div class="section" style="width: 30%; text-align: left;">
        <div style="padding-left: 10px;">
            <p>Augment</p>
        </div>
    </div>
    <div class="section" style="width: 10%;">
        <div style="display: flex; justify-content: center;">
            <div class="SLetter" style="margin: 6px 0;">
                <p style="border: 0; margin:0; padding:0;">S</p>
            </div>
        </div>
    </div>
    <div class="section" style="width: 20%;">
        <p>Avg Place</p>
    </div>
    <div class="section" style="width: 40%; text-align: left">
        <div style="padding-left: 10px;">
            <p>Description</p>
        </div>
    </div>
</div>
<style>
    
        .SLetter{
            height: 32px;
            width: 32px;
            background-color: #f05867;
            border-radius: 3px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 25px;
            font-weight: 600;
            color: black;
        }

        .augment{
            font-weight: 500;
            font-size: 18px;
            display: flex;
            background-color: #22242f;
            color: white;
            height: 44px;
            justify-content: center;
            align-items: center;
            border: 1px solid #5e5d5d;
            border-top: 0;
            border-right: 0;
        }
        .augment .section{
            border-right: 1px solid #5e5d5d;
        }

        p{
            margin: 9px;
        }

        .second{
            background-color: #2d2f3a;
        }
</style>