<script>
    import { Luuk_tol_trademark } from '$lib';
    import { Nav_bar } from '$lib';
    import { Main_heading } from '$lib';
    import { Background } from '$lib';
</script>

<div class="grid">

    <header>
        <Nav_bar />
    </header>

    <main>
        <Main_heading />
    </main>

    <footer class="view-transition-to">
        
        <Luuk_tol_trademark />

        <article class="about-me-container">

            <p class="about-me-text">Hoe-ist! My name is Luuk Tol, and I'm a Front-End Development student at the HVA (University of Applied Sciences Amsterdam). 
            This site is my Digital Canvas—a personal space where you can see all my goofs and try-outs. Keep in mind iy may not be the best, but atleast I learned something from it. 
            It's my collection of experiments. I explore new technologies (whenever I have time), and try to push my creative boundaries. 
            So please, scroll around, and see what I have been working on, and hopefully you learn something new too.</p>

        </article>

    </footer>

</div>

<Background />


<style>
/* ---------------------------------------------      Height function that changes height with media queries      -------------------------------------------------*/

.grid{
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
        align-self: center;
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

/* ---------------------------------------------      ABOUT-ME CONTENT    -------------------------------------------------*/

    .about-me-text{
        font-size: clamp(0.7rem, 3vw, 1.75rem);
        margin: 0;
        animation: animation_left-slide-in 1.3s ease-in-out;
    }

    .about-me-container{
        position: relative;
        display: flex;
        align-items: center;
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