<script>
 export let message;
 export let showModal = false;
 export let isPromo = false;
</script>
{#if showModal}
<!-- onclick presets to parent or child based on modal function invoked on app.svelteHTML. self is an event modifier which only allows you to click on the backdrop to toggle the event handler.  you can set this to any div/p/etc..-->
<div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
        <video width= "400" height="200" autoplay>
             <source src="https://www.youtube.com/watch?v=_n5E7feJHw0&ab_channel=darkchia00" type=video/mp4>
                <track kind="captions">
        </video>
        <p style='color: black'><strong>{message}</strong></p>
    </div>
</div>
{/if}
<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.468)
    }
    .modal{
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
    .promo .modal {
        background: crimson;
    }
</style>