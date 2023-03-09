<script>
    import MovieCards from "./MovieCards.svelte";
    export let savedMovies
    export let watchlist


    $: console.log('Det her er watchlist: ' + savedMovies)
</script>

<main class='page'>
    <h1>Here are the movies you would like to watch</h1>
    <div class="results">
        {#each savedMovies as movie, index}
                <MovieCards {movie} index = {index}  bind:watchlist bind:savedMovies/>
        {/each}
    </div>
</main>

<style>
        .results{
        display:grid;
        grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
        justify-content: center;
        align-items: center;
        grid-gap:.5rem;
        width:100vw;
        padding:.8rem;
        overflow: scroll;
    }
</style>