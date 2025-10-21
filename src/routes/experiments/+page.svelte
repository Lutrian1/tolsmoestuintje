<script>
    import { beforeNavigate } from '$app/navigation';
    import { onMount } from 'svelte';

    // Voor elke route in experiment, maar hier een nieuwe route aan als je nieuwe code hebt.
    const experimentRoutes = [
		{ date: '11-02-2025', name: 'Mouse draw on hover', type: 'Javascript', path: '/experiments/mousedraw' },
		{ date: '15-02-2025', name: 'Particle splash on button click', type: 'CSS-Only', path: '/experiments/particlesplash' }
	];

    // Adding block so the site doesn't follow the grid used in the homepage
	onMount(() => {
		document.body.style.display = 'block';

		beforeNavigate(() => {
			document.body.style.display = 'block';
		});
	});
</script>

<h1><span>MY</span> <span>EXPERIMENTS</span></h1>

<nav>
	<ul>
		{#each experimentRoutes as route}
			<li>
                <aside>{route.type}</aside>
                <a href={route.path}>{route.name}</a>
                <aisde>{route.date}</aisde>
            </li>
		{/each}
	</ul>
</nav>

<style>

/* ---------------------------------------------      Global functions, Devines if it uses my grid layout, or something else     -------------------------------------------------*/
    h1{
        font-family: var(--main-font);
        color: var(--main-accent-color);
        position: relative;
        width: 100%;
        display: flex;
        align-items: center;
        flex-direction: column;
        line-height: 10vw;

        span:first-child{
            color: var(--heading-accent-color);
            font-size: 7vw;
            display: flex;
            width: 80%;
            align-items: baseline;
        }

        span:nth-child(2){
            font-size: 15vw;
        }
    }
</style>