<script context="module">
	// Fetch movies
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${
				import.meta.env.VITE_API
			}&language=en-US&page=1`
		);

		const data = await res.json();
		if (res.ok) {
			return {
				props: { popular_movies: data.results }
			};
		}
	}
</script>

<script>
	import PopularMovies from '../components/PopularMovies.svelte';
	import SearchMovies from '../components/SearchMovies.svelte';
	import { fly } from 'svelte/transition';

	export let popular_movies;
</script>

<section in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 200 }}>
	<SearchMovies />
	<PopularMovies {popular_movies} />
</section>
