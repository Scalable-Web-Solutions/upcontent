<script lang="ts" module>
	declare global {
		interface Window {
			analytics: {
				init: (config?: any) => void;
				trackPageview?: () => void;
				trackEvent?: (type: string, fields?: object) => void;
			};
			firebase: any;
		}
	}
</script>

<script lang="ts">
	import { onMount } from 'svelte';
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
    import Nav from './comp/Nav.svelte';
	
	let { children } = $props();

	onMount(() => {
		function initTracking()
		{
			if(window.analytics){
				window.analytics.init({project: 'upcontent-hu'});
				window.analytics.trackPageview();
			}
			else{
				console.log('Analytics not initialized');
			}
		}
		initTracking();
		
	})
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="overflow-x-hidden">
	<Nav />
	{@render children?.()}
</main>
