<script>
    import Header from "../components/Header.svelte";
    import Augment from "../components/Augment.svelte";
    // export let ChamionCost;
  
  </script>
  
  <div>
    <div style="text-align: center;">
       <Header />
       <div style="display: flex; justify-content:center; align-items:center;">
            <div class="augmentContainer">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <div class="searchBox">
                        <div class="input-icons">
                            <svg class="icon" xmlns="http://www.w3.org/2000/svg" fill="#757575" height="25" width="25" viewBox="0 0 24 24"><g data-name="Layer 2"><path d="m20.71 19.29-3.4-3.39A7.92 7.92 0 0 0 19 11a8 8 0 1 0-8 8 7.92 7.92 0 0 0 4.9-1.69l3.39 3.4a1 1 0 0 0 1.42 0 1 1 0 0 0 0-1.42zM5 11a6 6 0 1 1 6 6 6 6 0 0 1-6-6z" data-name="search"/></g></svg>
                            <input type="text" class="input-field" placeholder="Seach Augment">
                        </div>
                    </div>
                    <div class="updateContainer">
                        <p style="padding: 0; margin: 0;">Last updated: 19, Aug 2022</p>
                    </div>
                </div>
                <div>
                    <div  class="augmentHead">
                        <div style="width: 30%;">
                            <p>Augment</p>
                        </div>
                        <div style="width: 10%;">
                            <p>Tier</p>
                        </div>
                        <div style="width: 60%;">
                            <p>Description </p>  
                        </div>
                    </div>
                    <Augment Description='If you have exactly 2 copies of a champion on your board, they both gain 22 Attack Damage, Ability Power, Armor, and Magic Resist. When you upgrade to 3-star, gain a 2-star copy.'/>
                </div>
        </div>
       </div>
    </div>
  </div>
  
  
  <style>
        .augmentHead{
            font-weight: 500;
            margin-top: 20px;
            font-size: 18px;
            display: flex;
            background-color: #22242f;
            color: white;
            height: 38px;
            justify-content: center;
            align-items: center;
            border: 1px solid #5e5d5d;
        }

        p{
            margin: 0;
        }
        .searchBox div input{
            min-width: 225px;
            padding-top: 3px;
            font-size: 16px;
            font-weight: 600;
            padding-left: 8px;
            height: 32px;
            background-color: #2d2f3a;
            border: 1px solid #5e5d5d;
            
        }

        .searchBox div input:active{
            border: none;
        } 

        .augmentContainer{
          width: 980px;
        }

        @media(max-width:1200px){
          .augmentContainer{
            max-width: 83%;
          }
        }
        @media(max-width:580px){
            .augmentContainer{
              width: 90%
          }
        }

      .updateContainer {
          background-color: #2d2f3a;
          border: 1px solid #5e5d5d;
          color: white;
          padding: 6px 10px;
          margin: 0;
          
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
  </style>
  