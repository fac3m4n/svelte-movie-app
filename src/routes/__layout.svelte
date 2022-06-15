<script>
	import global from '../../src/global.css';
	import Nav from '../../src/components/Nav.svelte';
</script>

<svelte:head>
	<title>Movie DB</title>
</svelte:head>

<Nav />

<!-- All other web data needs to be in slot -->
<slot />
