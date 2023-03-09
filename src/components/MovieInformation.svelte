<script>
    export let movie
    export let savedMovies
    export let watchlist
    let rating    

    rating = movie.vote_average.toFixed(1);

    
</script>



<main>

    <div id="top">
        <div style="text-align: left; display: grid; place-items: center; font-weight: bold;" class="titel">
            {#if movie.title.length >= 40}
                <div style="style='font-size: 1rem;'" class="big">
                    {movie.title}
                </div>
            {:else}
                <div style='font-size: 1.5rem;' class="small">
                    {movie.title}
                </div>
            {/if}
        </div>
        <div style="text-align: center; display: grid; place-items: center;" class="rating">
            <h2>{rating}/10</h2>
        </div>
    </div>
    
    <div id="mid">
        <div class="description">
            <h3>Description:</h3>
            {movie.overview}
        </div>
    </div>
    <div id="bund">
        <div class="watchlist">
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <svg style= "cursor:pointer;" on:click={()=> {
                watchlist = [...watchlist, movie]  
                console.log("Yo! du klikkede på hjerte") 
            }} xmlns="http://www.w3.org/2000/svg" height="48" width="48"><path d="m24 41.95-2.05-1.85q-5.3-4.85-8.75-8.375-3.45-3.525-5.5-6.3T4.825 20.4Q4 18.15 4 15.85q0-4.5 3.025-7.525Q10.05 5.3 14.5 5.3q2.85 0 5.275 1.35Q22.2 8 24 10.55q2.1-2.7 4.45-3.975T33.5 5.3q4.45 0 7.475 3.025Q44 11.35 44 15.85q0 2.3-.825 4.55T40.3 25.425q-2.05 2.775-5.5 6.3T26.05 40.1ZM24 38q5.05-4.65 8.325-7.975 3.275-3.325 5.2-5.825 1.925-2.5 2.7-4.45.775-1.95.775-3.9 0-3.3-2.1-5.425T33.5 8.3q-2.55 0-4.75 1.575T25.2 14.3h-2.45q-1.3-2.8-3.5-4.4-2.2-1.6-4.75-1.6-3.3 0-5.4 2.125Q7 12.55 7 15.85q0 1.95.775 3.925.775 1.975 2.7 4.5Q12.4 26.8 15.7 30.1 19 33.4 24 38Zm0-14.85Z"/></svg>
            
        </div>
        <div class="RatedMovies">
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <svg style= "cursor:pointer;" on:click={()=> {
                savedMovies = [...savedMovies, movie]
                console.log("Yo! du klikkede på rating")
                console.log(savedMovies)
            }}
                xmlns="http://www.w3.org/2000/svg" height="48" width="48"><path d="m16.15 37.75 7.85-4.7 7.85 4.75-2.1-8.9 6.9-6-9.1-.8L24 13.7l-3.55 8.35-9.1.8 6.9 6ZM11.65 44l3.25-14.05L4 20.5l14.4-1.25L24 6l5.6 13.25L44 20.5l-10.9 9.45L36.35 44 24 36.55ZM24 26.25Z" 
            oncl/></svg>
        </div>

    </div>

</main>

<style>
	:global(*, body){
		box-sizing: border-box;
		margin:0;
		padding:0;
	}
    #mid{
        /* border: solid 2px black; */
    }
    #bund{
        display: grid;
        position: relative;
    }
    .RatedMovies{
        position: absolute;
        right: .5rem;
        bottom: .3rem;
    }
    .watchlist{
        position: absolute;
        left: .5rem;
        bottom: .3rem;
    }

    #top{
        display: grid;
        /* border: solid 2px black;  */
        grid-template-columns: 8.5fr 1.5fr;   
    }
    
    .titel{
        /* border: solid 1px black;     */
        
    }
    .rating{
        /* border: solid 1px black;     */
    }
    .description{
        display: grid;
        /* place-items: center; */
        padding: 3rem;
        padding-top: 5rem;
        text-align: left;
    }

    main{
        display: grid;
        grid-template-rows: 1.5fr 10fr 1.5fr;
        height: 430px;
    }
    h3{
        text-decoration: underline;
        font-weight: bold;
        /* position: absolute;
        left: 0;     */
    }

</style>