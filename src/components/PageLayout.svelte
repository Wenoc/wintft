<script>

</script>

<div class="container">
    <div class="leftpane">
        <slot name="left">
            
        </slot>
    </div>
    <div class="middlepane">
        <slot name="middle">

        </slot>
    </div>
    <div class="rightpane">
        <slot name="right">

        </slot>
    </div>
  </div>

<style>

@media (max-width: 980px) 
	{
        .leftpane{
            display: none;
        }
        .rightpane{
            display: none;
        }
        .container{
          display: flex;
          justify-content: center;
          
        }
    }

.container {
  width: 100%;
}

.leftpane {
    width: 22%;
    float: left;
    background-color: rosybrown;
    border-collapse: collapse;
}

.middlepane {
    width: 56%;
    float: left;
}

.rightpane {
  width: 22%;
  float: right;
  border-collapse: collapse;
}
</style>