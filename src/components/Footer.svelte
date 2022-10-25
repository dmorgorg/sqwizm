<script>
    export let quiz;
</script>

<footer>
   
    {#if quiz.isLoggedIn}
        hello, {quiz.name}
    {:else}
        not logged in footer
    {/if}
</footer>

<style>
    footer {
        background-color: yellow;
        display: flex;
        width: 100%;
        margin: 0;
        border: none;
    }
</style>
