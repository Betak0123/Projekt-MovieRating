<script>
	import Menuitem from './components/Menuitem.svelte'
	import Frontpage from './components/Frontpage.svelte'
    import FindMovie from './components/FindMovie.svelte';
    import Watchlist from './components/Watchlist.svelte';
    import SavedMovies from './components/SavedMovies.svelte';
	let menu = ['Frontpage', 'Find Movie', 'Watchlist', 'Rated movies']
	let activePage = menu[1]

	let watchlist = []
	let savedMovies = []

</script>

<header>
	{#each menu as item}
		<Menuitem bind:activePage={activePage} title={item} />
	{/each}
</header>
<main>
	{#if activePage == menu[0]}
		<Frontpage/>
	{:else if  activePage == menu[1]}
		<FindMovie bind:savedMovies bind:watchlist/>
	{:else if  activePage == menu[2]}
		<Watchlist bind:savedMovies bind:watchlist={watchlist}/>
	{:else if  activePage == menu[3]}
		<SavedMovies bind:savedMovies bind:watchlist/>
	{/if}
</main>

<style>
	:global(*, body){
		box-sizing: border-box;
		margin:0;
		padding:0;
	}
	:global(.page){
		display:grid;
		place-items:center;
		height:90vh;
	}
	header{
		display:grid;
		height:10vh;
		grid-auto-flow:column;
		place-items:center;
		background:black;
	}
	main {
		display:grid;
		place-items:center;
		/* background-color: black;x */
	}

	h1 {
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 100;
	}
</style>