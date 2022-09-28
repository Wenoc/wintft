<script>
</script>

<div class="container">
  <div class="leftpane">
    <slot name="left" />
  </div>
  <div class="middlepane">
    <slot name="middle" />
  </div>
  <div class="rightpane">
    <slot name="right" />
  </div>
</div>

<style>
  .container {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .container div {
    width: 100%;
  }

  .middlepane {
  }

  .leftpane {
    margin-top: 260px;
    display: flex;
    justify-content: center;
  }

  .rightpane {
    margin-top: 260px;
    display: flex;
    justify-content: center;
  }
</style>
