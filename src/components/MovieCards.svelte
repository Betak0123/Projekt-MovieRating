<script>
    export let movie // javascript objekt med en hel opskrift
    export let index
    import MovieInformation from './MovieInformation.svelte';
	import {blur} from 'svelte/transition'
	import {fade} from 'svelte/transition'
	import {fly} from 'svelte/transition'
	import {scale} from 'svelte/transition'
    export let opened
    export let savedMovies
    export let watchlist


    // $: console.log(opened)

    let BaseURL = 'https://image.tmdb.org/t/p/'
    let size = 'original'


    let y
    console.log(index)

    console.log(movie)
    let active = false
</script>

<svelte:window bind:scrollY={y}/>


    {#if !active}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
         <div in:fly="{{ y: 200, duration: 500 }}" out:blur on:click={() => {
            if (!opened){
                opened = !opened
                active = !active }} 
            }
         class={active ? 'active' : 'card'} style='background-image:url({BaseURL+size+movie.poster_path});'>
         
         
         
        {#if !movie.poster_path}
        <h2>{movie.title}</h2>
        {/if}

        </div>
        {:else}
        
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <div in:scale out:scale id="InfoContainer">
            <div class={active ? 'active card' : 'card'} style='background-image:url({BaseURL+size+movie.poster_path});'>
            
           <div on:click={() => {
            if(opened){
                opened = !opened
                active = !active }}
            }
            class="cross">
            <svg style="cursor: pointer;" xmlns="http://www.w3.org/2000/svg" height="48" width="48"><path d="m12.45 37.65-2.1-2.1L21.9 24 10.35 12.45l2.1-2.1L24 21.9l11.55-11.55 2.1 2.1L26.1 24l11.55 11.55-2.1 2.1L24 26.1Z"/></svg>
           </div> 
           </div>
           <div id="information">
            <MovieInformation {movie} bind:watchlist bind:savedMovies />
           </div>
    
        </div>
    {/if}






<style>
    	:global(*, body){
		box-sizing: border-box;
		margin:0;
		padding:0;
	}
    .card{
        height:300px;
        width:100%;
        display:grid;
        place-items:center;
        font-weight: 100;
        /* color:white; */
        border-radius:1rem;
        border: 2px solid black;
        /* background-color: black; */
        position: relative;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }
    #InfoContainer{
        display: grid;
        position: fixed;
        top: 50%;
        left: 50%;
        margin-top: -215px; /* half of the height */
        margin-left: -450px; /* half of the width */
        width: 900px;
        height: 430px;
        grid-auto-flow: column;
        border: solid 1px black;
        z-index: 5;
        border-radius: 1rem;
        background-color: gray;
    }
    .cross{
        position: absolute;
        top: .5rem;
        left: .5rem;
        fill: white;
    }
    #information{
        display: grid;
        height: 430px;
        width: 600px;
    }

    h2{
        background-color: rgba(129, 129, 129, 0.742);
        color: black;
        border-radius: 1rem;
        padding: .5rem;
        font-size: larger;
        z-index: 2;
    }
    .active{
        transition: all 1s ease-in-out;
        height:430px;
        width:300px;
        background-size: cover;
        display: grid;
        grid-template-rows: 1fr 1fr 1fr;
        border-top-left-radius: 1rem;
        border-bottom-left-radius: 1rem;
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
        padding: 1rem;
        z-index: 2;
    }
    
    p{
        background-color: rgba(255, 255, 255, 0.742);
        color: black;
        border-radius: 1rem;
        padding: .5rem;
        font-weight: 400;
        width: fit-content;
        border: 1px solid black;
    }


</style>