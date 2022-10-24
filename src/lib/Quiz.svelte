<script>
    import { onMount, afterUpdate } from "svelte";
    import qwiz from "../qwiz";
    import Header from "./Header.svelte";
    import Footer from "./Footer.svelte";
    let quizId = qwiz.quizId; // identifier for label object holding quiz
    let quiz = []; // the object holding quiz
    let isLoggedIn = false;

    onMount(() => {
        if (localStorage.getItem(quizId)) {
            quiz = JSON.parse(localStorage.getItem(quizId));
            isLoggedIn = true;
        } else {
            isLoggedIn = false;
        }
    });
    function setLocalStorage() {
        localStorage.setItem(quizId, JSON.stringify(quiz));
    }
    afterUpdate(() => {
        if (isLoggedIn) setLocalStorage();
    });
</script>

<main>
    <Header {qwiz} />

    <section class="views">
        {#if isLoggedIn}
            logged in
        {:else}
            not logged in
        {/if}
    </section>

    <Footer {isLoggedIn} />
</main>

<style>
    main {
        align-items: center;
        display: flex;
        flex-direction: column;
        height: 100vh;
        justify-content: space-between;
    }
</style>
