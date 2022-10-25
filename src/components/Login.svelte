<script>
    export let quiz;
    let name, studentId;
    $: isEmpty = !name || !studentId;
    const handleLoginSubmit = () => {
        console.log("handling...");
        quiz.isLoggedIn = true;
        quiz.name = name;
        quiz.studentId = studentId;
        // quiz = quiz;
    };
</script>

<div class="login-form ">
    <section class="form">
        <h2>login</h2>
        <form on:submit|preventDefault={handleLoginSubmit}>
            <div class="form-control">
                <label for="name">Name:</label>
                <input
                    type="text"
                    id="name"
                    autocomplete="off"
                    bind:value={name}
                />
            </div>
            <div class="form-control">
                <label for="id">Student ID:</label>
                <input
                    type="text"
                    id="id"
                    autocomplete="off"
                    bind:value={studentId}
                />
            </div>
            {#if isEmpty}
                <p class="form-empty">
                    please fill out both the form fields above
                </p>
            {/if}
            <button type="submit" disabled={isEmpty}>Submit</button>
        </form>
    </section>
</div>

<style>
    label {
        display: block;
    }
    .form-control {
        margin: 1em 0;
    }
</style>
