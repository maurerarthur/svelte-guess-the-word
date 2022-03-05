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

<div class="h-100 d-flex flex-column align-items-center justify-content-center">
    <div>
        {#each userInput as _, input}
            <input
                type='text'
                class={userInput[input] == word[input] ? 'green' : ''}
                bind:value={userInput[input]}
            />
        {/each}
    </div>
    {#if isWordDiscovered}
        <p>That's right. The word is {word}</p>
    {/if}
</div>

<style>
    input {
        height: 30px;
        width: 30px;
    }

    .green {
        color: green 1px solid;
    }
</style>