<script>
    import { beforeNavigate } from '$app/navigation';
    import { onMount } from 'svelte';

    // Voor elke route in experiment, maar hier een nieuwe route aan als je nieuwe code hebt.
    const experimentRoutes = [
		{ date: '11-02-2025', name: 'Mouse draw on hover', type: 'J-Script', path: '/experiments/mousedraw' },
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

<main>
    <h1><span>MY</span> <span>EXPERIMENTS</span></h1>

    <article>
        <ul>
            {#each experimentRoutes as route}
                <li>
                    <aside>{route.type}</aside>
                    <a href={route.path}>{route.name}</a>
                    <aside>{route.date}</aside>
                </li>
            {/each}
        </ul>
    </article>
</main>

<footer>
    <a href="/">Go back</a>
</footer>


<style>
    h1{
        font-family: var(--main-font);
        color: var(--main-accent-color);
        position: relative;
        width: 100%;
        display: flex;
        align-items: center;
        flex-direction: column;
        line-height: 10vw;
        margin: 4rem 0 5rem 0;

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

    article{
        display: flex;
        justify-content: center;
    }

    ul{
        display: flex;
        justify-content: center;
        flex-direction: column;
        padding: 0;
        margin: 0;
    }

    li{
        font-size: clamp(1.1rem, 5vw, 3.5rem);
        list-style: none;
        display: flex;
        border: solid 0.1rem var(--main-color);
        flex-direction: row;
        min-height: 8rem;

        *{
            padding: 0 2vw;
            border: inherit;
            display: flex;
            align-items: center;
        }

        a{
            flex-grow: 2;
            text-decoration: none;
            color: var(--main-color);
        }
        
        aside{
            width: 14cqw;
            max-width: 15rem;
        }

    }

    footer{
        position: fixed;
        top: 2rem;
        left: 2rem;
    }
    
</style>