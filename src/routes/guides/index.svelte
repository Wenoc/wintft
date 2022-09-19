<script>
  import BlogItem from "../../components/BlogItem.svelte";

  let kereses;

</script>

<div class="page">
    <div class="blogContainer">
        <div class="newestBlog" style="background: url('/blogBackground/bg1.png') top/cover">
            <div class="topSection">
                <div>
                    <p>Newest</p>
                </div>
                <div>
                    <p>2022/05/25</p>
                </div>
            </div>
            <div class="newTitle">
                <p>Teamfight Tactics Patch 12.15 Notes & Breakdown</p>
            </div>
        </div>
        <div class="highlightedContainer">
            <div class="highlighted" style="background: url('/blogBackground/bg2.png') top/cover">
                <div class="highlightedContent">
                    <div style="text-align: right;">
                        <p>August 15, 2022</p>
                    </div>
                    <div style="position: relative;">
                        <p style="position: absolute; bottom: 0; right: 0;">Teamfight Tactics Patch 12.15 Notes & Breakdown</p>
                    </div>
                </div>
            </div>
            <div class="highlighted" style="background: url('/blogBackground/bg3.png') top/cover">
                <div class="highlightedContent">
                    <div style="text-align: right;">
                        <p>August 15, 2022</p>
                    </div>
                    <div style="position: relative;">
                        <p style="position: absolute; bottom: 0; right: 0;">Teamfight Tactics Patch 12.15 Notes & Breakdown</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="searchContainer">
        <div class="searchBox">
           <div class="input-icons">
              <svg class="icon" xmlns="http://www.w3.org/2000/svg" fill="#757575" height="25" width="25" viewBox="0 0 24 24">
                 <g data-name="Layer 2">
                    <path d="m20.71 19.29-3.4-3.39A7.92 7.92 0 0 0 19 11a8 8 0 1 0-8 8 7.92 7.92 0 0 0 4.9-1.69l3.39 3.4a1 1 0 0 0 1.42 0 1 1 0 0 0 0-1.42zM5 11a6 6 0 1 1 6 6 6 6 0 0 1-6-6z" data-name="search"/>
                 </g>
              </svg>
              <input type="text" class="input-field" placeholder="Seach Augment" bind:value="{kereses}">
           </div>
        </div>
        <div class="updateContainer">
           <p style="padding: 0; margin: 0;">Last updated: 19, Aug 2022</p>
        </div>
     </div>
     <div class="otherBlogs">
        <BlogItem title="New player guide"/>
        <BlogItem />
        <BlogItem />
     </div>
</div>

<style>
    .highlightedContent{
        height: 95%;
        padding: 5px 10px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .highlightedContent div{
        height: 100%;
    }

    .otherBlogs{
        max-width: 1005px;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
    }

    P{
        margin: 0;
        padding: 0;
        color: white;
    }
    .topSection{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 10px 20px;
        color: white;
        font-size: 22px;
    }
    .newTitle{
        color: white;
        font-size: 26px;
        padding: 20px;
    }

    .page{
        display: flex;
        align-items: center;
        flex-direction: column;
        margin-top: 200px;
    }
    .blogContainer{
        width: 980px;
        height: 400px;
        display: flex;
        justify-content: center;
    }

    .newestBlog {
        cursor: pointer;
        height: 400px;
        width: 65%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .highlightedContainer{
        margin-left: 16px;
        width: 35%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    
    .highlighted{
        cursor: pointer;
        width: 100%;
        height: 192px;
    }

    .searchContainer{
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 980px;
        min-width: 980px;
        margin: 0 auto;
        margin-bottom: 8px;
        margin-top: 70px;
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
            outline: none;
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