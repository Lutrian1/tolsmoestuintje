<script>
    import { onMount } from 'svelte';
    import { beforeNavigate } from '$app/navigation';

    import { Luuk_tol_trademark } from '$lib';
    import { Background } from '$lib';
    import { Nav_bar } from '$lib';
    import { Main_heading } from '$lib';

    // Adding grid so the site follows the grid in the global-stylesheet, beforenavigate: https://svelte.dev/docs/kit/$app-navigation
	onMount(() => {
		document.body.style.display = 'grid';

		beforeNavigate(() => {
			document.body.style.display = 'grid';
		});
	});

</script>

<header>
    <Nav_bar />
</header>

<main>
   <Main_heading />
</main>

<footer>
    <Luuk_tol_trademark />
</footer>

<Background />

<style>

/* ---------------------------------------------      GRID      -------------------------------------------------*/

    /* GRID Template areas */
    footer { grid-area: footer; }
    main { grid-area: main; }
    header { grid-area: header; }

/* ---------------------------------------------      ORDER      -------------------------------------------------*/

    header {
        order: 3;
    }

    main {
        order: 2;
    }

    footer {
        order: 1;
    }

/* ---------------------------------------------      HEADER STYLING     -------------------------------------------------*/

header{
    display: flex;
    justify-content: center;
    flex-direction: column;
    container-name: header;
    container-type: inline-size;
    z-index: 1;
}

/* ---------------------------------------------      FOOTER STYLING     -------------------------------------------------*/

    footer{
        display: grid;
        gap: 1.5rem;
        grid-auto-columns: 1fr; 
        grid-template-columns: 0.4fr 1.5fr; 
        grid-template-rows: 1fr; 

        /* CONTAINER NAMES */

        container-type: inline-size;
        container-name: footer;

        z-index: 1;
    }
</style>