<script>
    import { goto } from '$app/navigation';
	import './viewtransitionflower.css';

	function navigateWithTransition(event) {
		event.preventDefault();
		const href = event.currentTarget.getAttribute('href');

		// Use the View Transitions API if available
		if (document.startViewTransition) {
			document.startViewTransition(async () => {
				await goto(href);
			});
		} else {
			// fallback
			goto(href);
		}
	}
</script>

<main>
	<div class="flower"></div>
	<a href="/experiments/flowerviewtrans/navto" on:click={navigateWithTransition}>Start transition</a>
	<p>This view transition was used for CSS-Day, you can see more in my blog about this. It uses the new CSS View Transitions API. The support for this is still limited.</p>
</main>

<style>
	:root {
		--clockwise: large cw;
	}

	.flower {
		margin-bottom: 2rem;
		width: 100px;
		height: 100px;
		view-transition-name: flower;
		background: var(--main-accent-color);
		aspect-ratio: 1;
		clip-path: shape(
			from 75.4762724747% 50%,
			arc to 57.872601148% 74.229374948% of 18.5095954079% var(--clockwise),
			arc to 29.3892626146% 64.974577244% of 18.5095954079% var(--clockwise),
			arc to 29.3892626146% 35.025422756% of 18.5095954079% var(--clockwise),
			arc to 57.872601148% 25.770625052% of 18.5095954079% var(--clockwise),
			arc to 75.4762724747% 50% of 18.5095954079% var(--clockwise)
		);
	}

	p {
		max-width: 50rem;
		text-align: center;
		font-size: 2.5rem;
	}
</style>
