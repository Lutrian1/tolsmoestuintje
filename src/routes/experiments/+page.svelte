<script>
    import { beforeNavigate } from '$app/navigation';
    import { onMount } from 'svelte';

    // Adding grid so the site follows the grid in the global-stylesheet, beforenavigate: https://svelte.dev/docs/kit/$app-navigation
	onMount(() => {
		document.body.style.display = 'block';

		beforeNavigate(() => {
			document.body.style.display = 'block';
		});
	});
    
</script>

<h1><span>MY</span> <span>EXPERIMENTS</span></h1>

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