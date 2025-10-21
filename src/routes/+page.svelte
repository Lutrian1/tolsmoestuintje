<script>
    import { Luuk_tol_trademark } from '$lib';
    import { Nav_bar } from '$lib';
    import { Main_heading } from '$lib';

    import { beforeNavigate } from '$app/navigation';
    import { onMount } from 'svelte';

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

<style>
/* ---------------------------------------------      Functions and maths     -------------------------------------------------*/

@layer --website-height-function{/* --- (Verander dit nadat css @function heb geshipped -- */

    :root {
    --website-height-calc: 600vh;
    }

    @media (min-height: 150px) {
    :root {
        --website-height-calc: 500vh;
    }
    }

    @media (min-height: 180px) {
    :root {
        --website-height-calc: 400vh;
    }
    }

    @media (min-height: 190px) {
    :root {
        --website-height-calc: 350vh;
    }
    }

    @media (min-height: 200px) {
    :root {
        --website-height-calc: 350vh;
    }
    }

    @media (min-height: 300px) {
    :root {
        --website-height-calc: 250vh;
    }
    }

    @media (min-height: 390px) {
    :root {
        --website-height-calc: 200vh;
    }
    }

    @media (min-height: 460px) {
    :root {
        --website-height-calc: 150vh;
    }
    }

    @media (min-height: 560px) {
    :root {
        --website-height-calc: 135vh;
    }
    }

    @media (min-height: 620px) {
    :root {
        --website-height-calc: 115vh;
    }
    }

    @media (min-height: 710px) {
    :root {
        --website-height-calc: 100%;
    }
    }

}

/* ---------------------------------------------      Height function that changes height with media queries      -------------------------------------------------*/

:global(html), :global(body){
    height: var(--website-height-calc);
}

/* ---------------------------------------------      GRID - GRID-AREA NAMING / ORDER     -------------------------------------------------*/

@layer grid-naming-order{
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
}

/* ---------------------------------------------      GRID - HOMEPAGE      -------------------------------------------------*/

@layer grid-homepage{

    :root {
        --gap: 0.5rem;
        --columns: 16;
        --rows: 16; 
    }

    /* ---------------------------------------------     PHONE     -------------------------------------------------*/
    :global(body){
        grid-template-columns: repeat(var(--columns));
        grid-template-rows: repeat(var(--rows));
        min-height: 100%;
        gap: var(--gap);
        grid-template-areas:    
        ". . . . . . . . . . . . . . ."
        ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
        ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
        ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
        ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
        ". . . . . . . . . . . . . . ."
        ". . . main main main main main main main main main . . ."
        ". . . main main main main main main main main main . . ."
        ". . . main main main main main main main main main . . ."
        ". . . main main main main main main main main main . . ."
        ". . . . . . . . . . . . . . ."
        ". header header header header header header header header header header header header header ."
        ". header header header header header header header header header header header header header ."
        ". header header header header header header header header header header header header header ."
        ". header header header header header header header header header header header header header ."
        }
    /* ---------------------------------------------     TUSSEN GEDEELTE     -------------------------------------------------*/
    @media (min-width: 750px){
        :global(body){
            grid-template-columns: repeat(var(--columns));
            grid-template-rows: repeat(var(--rows));
            min-height: 100%;
            gap: var(--gap);

            grid-template-areas:    
            ". . . . . . . . . . . . . . ."
            ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
            ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
            ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
            ". footer footer footer footer footer footer footer footer footer footer footer footer footer ."
            ". . . . . . . . . . . . . . ."
            ". . . main main main main main main main main main . . ."
            ". . . main main main main main main main main main . . ."
            ". . . main main main main main main main main main . . ."
            ". . . main main main main main main main main main . . ."
            ". . . main main main main main main main main main . . ."
            ". . . . . . . . . . . . . . ."
            ". . header header header header header header header header header header header . ."
            ". . header header header header header header header header header header header . ."
            ". . header header header header header header header header header header header . ."
            ". . . . . . . . . . . . . . ."; 
        }
    }
    /* ---------------------------------------------     DESKTOP     -------------------------------------------------*/
    @media (min-width: 1150px){
        :global(body){
            grid-template-columns: repeat(var(--columns), 1fr);
            grid-template-rows: repeat(var(--rows), 1fr);
            min-height: 100%;
            gap: var(--gap);

            grid-template-areas:    
            ". . . . . . . . . . . . . . ."
            ". . footer footer footer footer footer footer footer footer footer footer footer . ."
            ". . footer footer footer footer footer footer footer footer footer footer footer . ."
            ". . footer footer footer footer footer footer footer footer footer footer footer . ."
            ". . footer footer footer footer footer footer footer footer footer footer footer . ."
            ". . . . . . . . . . . . . . ."
            ". . . main main main main main main main main main main . ."
            ". . . main main main main main main main main main main . ."
            ". . . main main main main main main main main main main . ."
            ". . . main main main main main main main main main main . ."
            ". . . main main main main main main main main main main . ."
            ". . . . . . . . . . . . . . ."
            ". . header header header header header header header header header header header header ."
            ". . header header header header header header header header header header header header ."
            ". . header header header header header header header header header header header header ."
            ". . . . . . . . . . . . . . ."; 
        }
    }

}

</style>