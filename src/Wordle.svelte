<script>
    const wordsLength = 5

    const words = [
        'glass',
        'mouse',
        'stare',
        'meter',
        'drive'
    ]

    const word = words[Math.floor(Math.random() * words.length)]

    let userInput = Array(wordsLength)

    let isWordDiscovered = false

    $: if(userInput.join('') == word) {
        isWordDiscovered = true
    }
</script>

<div class="background container-fluid">
    <div class="h-100 d-flex flex-column align-items-center justify-content-center">
        <h3 class="mb-4">Wordle</h3>
        <div>
            {#each userInput as _, input}
                <input
                    type="text"
                    class={userInput[input] == word[input] ? "correct_letter" : ""}
                    bind:value={userInput[input]}
                />
            {/each}
        </div>
        {#if isWordDiscovered}
            <p class="mt-4">That's right. The word is {word}</p>
        {/if}
    </div>
</div>

<style>
    :root {
        --purple: #503047;
        --green: #ADC698;
        --light-white: #D0E3C4;
    }

    @import url("https://fonts.googleapis.com/css2?family=League+Gothic&display=swap");

    input {
        height: 60px;
        width: 60px;
        margin: 5px;
        color: var(--purple);
        border: none;
        outline: none;
        text-align: center;
        font-size: 40px;
        font-family: "League Gothic", sans-serif;
    }

    h3 {
        font-family: "League Gothic", sans-serif;
        color: var(--light-white);
        text-transform: uppercase;
    }

    p {
        font-family: "League Gothic", sans-serif;
        color: var(--light-white);
    }

    .background {
        background-color: var(--purple);
    }

    .correct_letter {
        background-color: var(--green);
    }
</style>