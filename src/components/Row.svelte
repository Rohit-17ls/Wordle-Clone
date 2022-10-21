<script>
    import TailwindCss from '../TailwindCSS.svelte';
    import Grid from './Grid.svelte';
    export let word, correctIndices, existIndices;
    
    // console.log(correctIndices);
  


</script>
<TailwindCss/>

<div class="flex flex-row justify-center">
    {#each word as letter, ind}
        <Grid {letter} grad={correctIndices[ind] === 'correct'} exist={existIndices[ind] === 'exist'} incorrect = {existIndices[ind] === 'incorrect'}/>
        <!-- <Grid {letter} grad={ind}/> -->
    {/each}
</div>