<script>
    export let showPopUp = false;
</script>
{#if showPopUp}
<div class="popUp">
</div>
{/if}
<style>
        .popUp{
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background:  lightcoral;
    }
</style>