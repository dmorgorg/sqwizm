<script>
    import { onMount, afterUpdate } from "svelte";
    import qwiz from "../assets/qwiz";
    import Header from "./Header.svelte";
    import Footer from "./Footer.svelte";
    import Login from "./Login.svelte";

    let quizId = qwiz.quizId; // identifier for object holding this quiz is quizId
    let quiz = {}; // object holding state of the quiz
    quiz.isLoggedIn = false;
    // let isLoggedIn;

    onMount(() => {
        if (localStorage.getItem(quizId)) {
            quiz = JSON.parse(localStorage.getItem(quizId));
            quiz.isLoggedIn = true;
        }
    });
    function setLocalStorage() {
        localStorage.setItem(quizId, JSON.stringify(quiz));
    }
    afterUpdate(() => {
        // console.log("in afterUpdate");
        if (quiz.isLoggedIn) setLocalStorage();
    });
</script>

<main>
    <Header {qwiz} />

    <section class="views">
        {#if quiz.isLoggedIn}
            page views go here
        {:else}
            <Login bind:quiz />
        {/if}
    </section>


    <Footer {quiz} />
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
