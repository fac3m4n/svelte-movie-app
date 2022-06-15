<script>
	import MovieCard from './MovieCard.svelte';

	export let popular_movies;
</script>

<h3>Popular Moives</h3>

<div class="popular-movies">
	{#each popular_movies as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	h3 {
		padding: 0 1 rem;
	}

	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
	}
</style>
