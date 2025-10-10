<script>
    import { Splatter_behind_heading_SVG } from '$lib';
</script>
 
<section class="heading-1-wrapper">
        <h1>
            DIGITAL 
            <span>
                CANVAS
                <Splatter_behind_heading_SVG />
            </span>
        </h1>
    <p class="tip-p" aria-hidden="true">Mouse click to start painting!</p>
</section>

<style>
    
/* ---------------------------------------------      WRAPPER HEADING (BOX STYTLING)      -------------------------------------------------*/
    .heading-1-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
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
        display: none;
        opacity: 60%;
        margin: 0.5rem 0 0 0 ;
        @media (min-width: 950px){
            display: block;
        }

    }

    span{
        color: var(--heading-accent-color);
    }

</style>