<script>
    export let isSecond = false;
    // export let augment = '';
    // export let tier = '';
    // export let avgPlace = '';
    export let Description = '';

</script>

<div class="augment" class:second={isSecond} id="outer">
    <div class="container">
        <div class="section" style="width: 30%; text-align: left;">
            <div class="augmentNameSection" style="padding-left: 10px;">
                <p>Augment</p>
            </div>
        </div>
        <div class="section" style="width: 10%; justify-content: center;" id="inner">
            <div style="display: flex; justify-content: center;">
                <div class="SLetter" style="margin: 6px 0;">
                    <p style="border: 0; margin:0; padding:0;">S</p>
                </div>
            </div>
        </div>
        <div class="section" style="width: 60%; text-align: left;">
            <div style="padding-left: 10px;">
                <p class="description">{Description}</p>
            </div>
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

        .container{
            display: flex;
            flex: 1 1 auto;
            min-height: 50px;
        }

        .augment{
            font-weight: 500;
            font-size: 18px;
            display: flex;
            background-color: #22242f;
            color: white;
            justify-content: center;
            align-items: center;
            border: 1px solid #5e5d5d;
            border-top: 0;
            border-right: 0;
            min-height: 50px;
        }
        
        .augment .section{
            border-right: 1px solid #5e5d5d;
            font-weight: normal;
            display: flex;
            justify-content: start;
            align-items: center;
            flex: 1 1 auto;
        }

        .augmentNameSection{
            display: flex;
            justify-content: start;
            align-items: center;
        }

        p{
            margin: 9px;
        }

        .second{
            background-color: #2d2f3a;
        }

        .description{
            font-size: 14px;
        }
</style>