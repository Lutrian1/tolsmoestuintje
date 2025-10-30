<script>
    import { Luuk_tol_trademark } from '$lib';
    import { Nav_bar } from '$lib';
</script>

<div class="grid">

    <main>
        
        <Luuk_tol_trademark />

        <article class="about-me-container">

            <p class="about-me-text">Lorem ipsum dolor sit amet consectetur adipiscing elit. 
                Quisque faucibus ex sapien vitae pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. 
                Tempus leo eu aenean sed diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. 
                Iaculis massa nisl malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. 
                Ad litora torquent per conubia nostra inceptos himenaeos.</p>

            <p class="about-me-text">Lorem ipsum dolor sit amet consectetur adipiscing elit. 
                Quisque faucibus ex sapien vitae pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. 
                Tempus leo eu aenean sed diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. 
                Iaculis massa nisl malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. 
                Ad litora torquent per conubia nostra inceptos himenaeos.</p>

            <h3>Muziek</h3>

            <p class="about-me-text">Lorem ipsum dolor sit amet consectetur adipiscing elit. 
                Quisque faucibus ex sapien vitae pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. 
                Tempus leo eu aenean sed diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. 
                Iaculis massa nisl malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. 
                Ad litora torquent per conubia nostra inceptos himenaeos.</p>

            <p class="about-me-text">Lorem ipsum dolor sit amet consectetur adipiscing elit. 
                Quisque faucibus ex sapien vitae pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. 
                Tempus leo eu aenean sed diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. 
                Iaculis massa nisl malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. 
                Ad litora torquent per conubia nostra inceptos himenaeos.</p>

            <p class="about-me-text">Lorem ipsum dolor sit amet consectetur adipiscing elit. 
                Quisque faucibus ex sapien vitae pellentesque sem placerat. In id cursus mi pretium tellus duis convallis. 
                Tempus leo eu aenean sed diam urna tempor. Pulvinar vivamus fringilla lacus nec metus bibendum egestas. 
                Iaculis massa nisl malesuada lacinia integer nunc posuere. Ut hendrerit semper vel class aptent taciti sociosqu. 
                Ad litora torquent per conubia nostra inceptos himenaeos.</p>

        </article>

    </main>

    <footer class="view-transition-to">

        <Nav_bar />

    </footer>

</div>

<style>

/* ---------------------------------------------      Adds where the h2 should be placed     -------------------------------------------------*/

:global(h2){
    justify-content: flex-start;
}

/* ---------------------------------------------      Height function that changes height with media queries      -------------------------------------------------*/

.grid{
    height: var(--website-height-calc);
}

/* ---------------------------------------------      GRID - GRID-AREA NAMING / ORDER     -------------------------------------------------*/

@layer grid-naming-order{
    /* GRID Template areas */
    main { grid-area: footer; }
    footer { grid-area: header; }
}

main{
        grid-auto-flow: column;
        gap: 1.5rem;
        grid-auto-columns: 1fr; 
        grid-template-columns: 0.4fr 1.5fr; 
        grid-template-rows: 1fr; 

        /* CONTAINER NAMES */

        container-type: inline-size;
        container-name: footer;

        z-index: 1;

        @media (min-width: 750px){
            display: grid;
        }

}

/* ---------------------------------------------      ABOUT-ME CONTENT    -------------------------------------------------*/

    .about-me-text{
        font-size: clamp(0.7rem, 3vw, 1.75rem);
        margin: 1rem 0;
    }

    .about-me-container{
        position: relative;
        align-self: center;
        overflow: scroll;
        width: 100%;
        height: 600px;
        &::before{
            border-left: 2px solid black;
            content: "";
            display: block;
            height: 10rem;
            left: -2vw;
            position: absolute;
            width: 1px;
            z-index: 0;
        }
    }

    @container footer (width < 65.625rem) {
        .about-me-container{
            max-width: 45rem;
            .about-me-text{
                font-size: clamp(0.7rem, 3vw, 1.5rem);
            }
        }
    }
</style>
