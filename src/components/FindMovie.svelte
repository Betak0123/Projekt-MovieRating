<script>
    import Menuitem from "./Menuitem.svelte";
    import MovieCards from "./MovieCards.svelte";
    let opened = false
    export let savedMovies
    export let watchlist

    let q = 'dead'
    const api_key = '3c4d9114f886da9ce9eb61c82bcdf2c7'
    let movies = []
    $: console.log(q + ' is the query')
    // $: console.log(opened)
    $:  if (q.length > 0) {
        fetch(`https://api.themoviedb.org/3/search/movie?api_key=${api_key}&query=${q}`)
        .then(res => res.json())
        .then(json => {
            // console.log(json)
            movies = json.results
        })
    }
</script>

<main class='page'>
    <div class="searchbar">
        <input type="text" bind:value={q} on:click={()=>q=''}>
    </div>
    <div class="results">
        {#each movies as movie, index}
                    <MovieCards {movie} index = {index} bind:opened bind:watchlist bind:savedMovies/>
        {/each}
    </div>
</main>

<style>
    main{
        display:grid;
        grid-template-rows: 10vh 80vh;
        align-items: flex-start;
    }
    .searchbar{
        display:grid;
        background-color: cornflowerblue;
        width:100vw;
        height:100%;
        place-items:center;
    }
    input{
        border-radius: .6rem;
        width:60vw;
        text-align: center;
    }
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
    .movie{
        display:grid;
        min-width:100px;
        height:100px;
        grid-template-rows: 1fr 2fr;
        place-items:center;
        border:1px solid black;
        border-radius:5px;
        padding:1rem;
        transition:.1s ease-in-out all;
    }
 
    
</style>