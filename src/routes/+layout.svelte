<script>
	import signature from '$lib/assets/signature.avif';
	import '$lib/css/global-styles.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={signature} />
	<title>Digital Canvas</title>
</svelte:head>

{@render children?.()}

