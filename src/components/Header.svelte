<script>
    export let qwiz;
    let quiz = qwiz;
</script>

<header class={quiz.theme}>
    <h1 class='course'> {quiz.course}</h1>
    <div class='right-matter'>
        <div>{quiz.topic}</div>
        <div>{quiz.subTopic}</div>
    </div>
</header>

