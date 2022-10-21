<script>
  import TailwindCss from './TailwindCSS.svelte';
  import Main from './components/Main.svelte';
    import Spinner from './components/Spinner.svelte';
  let word;
  let fetchState = false;

  const fetchWords = async() => {
    const res = await fetch('https://raw.githubusercontent.com/Rohit-17ls/SVG-Repository/Svgs/API/word.json', {
      method: 'GET',
      // headers: {
      //   'X-RapidAPI-Key': 'dd3aaba847msh08e234778152c8ap1e7e44jsnc7843746e86c',
      //   'X-RapidAPI-Host': 'random-words5.p.rapidapi.com'
      // }
    });
    const data = await res.json();
    word = data[Math.floor(Math.random() * data.length)]
    fetchState = true;
  }
  fetchWords();
</script>


<TailwindCss/>
<main class="h-screen w-screen bg-primary-50">
  <div class="p-4 font grad-color">
    <h1 class="text-5xl font-bold">Wordle Clone</h1>
  </div>

  {#if fetchState}
    <Main {word}/>
  {:else}
      <Spinner/>
  {/if}
  
</main>

<style>
  
</style>