<script>
	import randomWords from 'random-words'

	const exactly = 1
	const words = randomWords({ exactly })
  const word = words[Math.floor(Math.random() * words.length)]

  let userInput = Array(words.toString().length)

  let isWordDiscovered = false

  $: if(userInput.join('') == word) {
    isWordDiscovered = true
	}
</script>

<div class="background container-fluid">
  <div class="h-100 d-flex flex-column align-items-center justify-content-center">
    <h3 class="mb-4">Guess the word!</h3>
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
      <p class="mt-4">That's right. The word is {word}.</p>
    {/if}
  </div>
</div>

<style>
  :root {
    --green: #ADC698;
  	--light-white: #D0E3C4;
  }

  input {
    height: 60px;
    width: 60px;
    margin: 5px;
    color: var(--purple);
    border: none;
    border-radius: 8px;
    outline: none;
    text-align: center;
    font-size: 40px;
    font-family: "League Gothic", sans-serif;
		text-transform: uppercase;
  }

  h3 {
  	color: var(--light-white);
		font-size: 50px;
    text-transform: uppercase;
  }

  p {
    font-family: "League Gothic", sans-serif;
		font-size: 25px;
    color: var(--light-white);
  }

  .correct_letter {
    background-color: var(--green);
  }
</style>