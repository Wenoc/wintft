<script>
    export let text;
</script>

<div class="NavBlogItem">
    <p class="textContent">{text}</p>
</div>
<style>
    .NavBlogItem{
        display: flex;
        align-items: center;
        cursor: pointer;
        font-size: medium;
        height: 40px;
        width: 250px;
        background-color: #2D2F3A;
        color: white !important;
        border: 1px solid #5e5d5d;
        border-collapse: collapse;
        padding-left: 15px;
    }
    .NavBlogItem:hover{
        background-color: #4b4e5c;
    }
</style>