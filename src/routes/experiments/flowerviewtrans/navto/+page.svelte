<script>
    import { goto } from '$app/navigation';
	import '../viewtransitionflower.css';

	function navigateWithTransition(event) {
		event.preventDefault();
		const href = event.currentTarget.getAttribute('href');

		if (document.startViewTransition) {
			document.startViewTransition(async () => {
				await goto(href);
			});
		} else {
			goto(href);
		}
	}
</script>

<div class="flower-new"></div>

<main>
	<a href="/experiments/flowerviewtrans" on:click={navigateWithTransition}>Go back</a>
</main>

<style>
	::view-transition-new(root) {
		opacity: 0;
		animation: none;
	}

	::view-transition-old(root) {
		opacity: 1;
		animation: none;
	}

	.flower-new {
		view-transition-name: flower;
		width: 100vw;
		height: 100vw;
		scale: 3;
		position: fixed;
		pointer-events: none;
		top: 0%;
		left: 0%;
		margin: 0;
		z-index: 1000;
	}
</style>
