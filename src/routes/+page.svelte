<script>
    import { Luuk_tol_trademark } from '$lib';
    import { Background } from '$lib';
    import { Nav_bar } from '$lib';
    import { Splatter_behind_heading_SVG } from '$lib';
</script>

<header>
    <Nav_bar />
</header>

<main>
    <div class="heading-1-wrapper">
        <h1>
            DIGITAL 
            <span>
                GARDEN
                <Splatter_behind_heading_SVG />
            </span>
        </h1>
    </div>
    <p class="tip-p">Mouse click to start painting!</p>
</main>

<footer>
    <Luuk_tol_trademark />
</footer>

<Background />

<style>

/* ---------------------------------------------      GRID      -------------------------------------------------*/

    /* GRID Template areas */
    footer { grid-area: footer; }
    main { grid-area: h1; }
    header { grid-area: header; }

    /* Wrapper heading (Heading box styling) */
    .heading-1-wrapper {
        display: flex;
        justify-content: center;
    }

/* ---------------------------------------------      MAIN CONTENT      -------------------------------------------------*/
    
    h1{
        position: relative;
        font-family: var(--heading-1-family);
        font-size: var(--heading-1);
        color: var(--heading-color);
        max-width: 34.375rem;
        text-align: center;
        z-index: 1;
        margin: 0;
        font-weight: 100;
        line-height: 0.9em;
        @media (min-width: 500px) and (max-width: 720px){
            max-width: 28.125rem;
        }
    }

    .tip-p{
        font-family: var(--heading-1-family);
        font-size: 1.5rem;
        text-align: center;
        opacity: 60%;
        margin: 0.5rem 0 0 0 ;
    }

    span{
        color: var(--heading-accent-color);
    }

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