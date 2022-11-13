<script>
  import ItemDetails from "../components/ItemDetails.svelte";
  import Champ from "../components/Champ.svelte";
</script>

<div>
  <Champ name={"ezreal"} Items={["Bloodthirster"]} />
</div>

<style>
  div {
    margin-top: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
