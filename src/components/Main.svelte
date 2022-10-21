<script>
    import TailwindCss from '../TailwindCSS.svelte';
    import Row from './Row.svelte';
    export let word;
    // console.log(word);

    const WORD_SIZE = 5;
    const ATTEMPTS = 6;
    let words = new Array(ATTEMPTS).fill('     '); // 5 empty spaces
    let wordIndex = 0;
    let letterIndex = -1;
    let correctIndices = new Array(ATTEMPTS);
    let existIndices =  new Array(ATTEMPTS);
    let gameOver = false;
    for(let i=0; i<ATTEMPTS; i++){
      correctIndices[i] = new Array(5).fill(false);
      existIndices[i] = new Array(5).fill(false);
    }



    const runComparisons = () => {
      let i=0;
      let corrects = 0;
      let typedWord = words[wordIndex].toUpperCase();
      for(let letter of typedWord){
        if(letter === word[i]) correctIndices[wordIndex][i] = 'correct';
        else if(word.includes(letter)) existIndices[wordIndex][i] = 'exist';
        else existIndices[wordIndex][i] = 'incorrect';
        corrects += (letter === word[i] ? 1 : 0);
        i++;
      }
      if(corrects === 5) gameOver = true;
    }

    window.addEventListener('keypress', (e) => {
      const letterAscii = e.key.charCodeAt(0);
      if((letterAscii >= 65 && letterAscii <= 90) || (letterAscii >= 97 && letterAscii <= 122)){
        if(letterIndex < WORD_SIZE-1 && e.key !== 'Enter'){
          letterIndex++;
          words[wordIndex] = words[wordIndex].substring(0, letterIndex) + e.key + words[wordIndex].substring(letterIndex+1, WORD_SIZE);
        }
        
      }

      if(letterIndex === WORD_SIZE-1 && e.key === 'Enter'){
        runComparisons();
        wordIndex++;
        if(wordIndex === 6) gameOver = true;
        letterIndex = -1;
      }

    

    });

    window.addEventListener('keydown', (e) => {
        // Backspace Handler
        const letterAscii = e.key.charCodeAt(0);
        if(letterAscii == 66 && letterIndex >= 0){
          words[wordIndex] = words[wordIndex].substring(0, letterIndex) + ' ' + words[wordIndex].substring(letterIndex+1, WORD_SIZE);
          letterIndex--;
        }
    })





</script>
<TailwindCss/>


  <section class="flex flex-col justify-center items-center text-white gap-2">
      <div class="text-2xl font-semibold block">G'Day mate, nice to have you at <span class="grad-color">Wordle-Clone</span></div>
      <div class="my-11 p-8 text-white-200">
        {#each words as word, ind}
          <Row {word} correctIndices = {correctIndices[ind]} existIndices = {existIndices[ind]}/>
        {/each}
      </div>
      <div class="my-0 p-8 grad-color text-4xl font-bold">{gameOver ? word : ''}</div>
  </section>



<style>
  
</style>
