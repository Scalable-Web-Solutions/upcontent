<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
    import Nav from './comp/Nav.svelte';
	
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="overflow-x-hidden">
	<Nav />
	{@render children?.()}
</main>
