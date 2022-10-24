<script>
    export let isLoggedIn = false;
</script>

<footer>
    {#if isLoggedIn}
        footer
    {:else}
        not logged in footer
    {/if}
</footer>

<style>
    footer {
        background-color: yellow;
        display: flex;
        width: 100%;
    }
</style>
