<script>
    import TailwindCss from '../TailwindCSS.svelte';
    export let letter, grad, exist, incorrect;
    // console.log(letter);


</script>
<TailwindCss/>

<!-- <span class="m-2 border-solid border-4 border-white-600 inline-block font-bold flex flex-row justify-center items-center w-20 h-20 text-center text-2xl"> -->
<span class="m-2 border-solid border-4 border-white-600 inline-block font-bold flex flex-row justify-center items-center w-20 h-20 text-center text-2xl {grad ? 'grad-border' : ''} {exist ? 'exist-border' : ''} {incorrect ? 'incorrect-border' : ''} ">
    {letter.toUpperCase()}
</span>