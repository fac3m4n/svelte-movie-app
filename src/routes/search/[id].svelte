<script context="module">
	// Fetch movies
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${
				import.meta.env.VITE_API
			}&language=en-US&query=${params.id}&page=1&include_adult=true`
		);

		const data = await res.json();
		if (res.ok) {
			return {
				props: { searched_movie: data.results }
			};
		}

		console.log(data);
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';

	export let searched_movie;
</script>

<div class="searched_movie">
	{#each searched_movie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	.searched_movie {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
	}
</style>
