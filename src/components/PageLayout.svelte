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
    width: 50%;
    display: flex;
  }

  .leftpane {
    width: 24.5%;
    margin-top: 260px;
    display: flex;
    justify-content: center;
  }

  .rightpane {
    width: 24.5%;
    widows: 470px;
    margin-top: 260px;
    display: flex;
    justify-content: center;
  }
</style>
