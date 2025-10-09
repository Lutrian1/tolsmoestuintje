<script>
    import { SplatterSVG } from '$lib';
    import { onMount } from 'svelte';

    let topTriangle;
    let bottomTriangle;

    onMount(() => {
        const handleMouseMove = (e) => {
            if (!topTriangle || !bottomTriangle) return;

            const mouseX = e.clientX;
            const windowWidth = window.innerWidth;
            
            // Calculate movement based on mouse position (normalized to 0 to 1)
            const moveAmount = 500;
            
            // Normalize mouse position to 0-1 range
            const normalizedX = mouseX / windowWidth;
            
            // Top triangle moves left when hovering (negative movement)
            const topMoveX = -normalizedX * moveAmount;
            
            // Bottom triangle moves right when hovering (positive movement)  
            const bottomMoveX = normalizedX * moveAmount;

            topTriangle.style.transform = `translateX(${topMoveX}px)`;
            bottomTriangle.style.transform = `translateX(${bottomMoveX}px)`;
        };

        // Add event listener to the entire document
        document.addEventListener('mousemove', handleMouseMove);

        return () => {
            document.removeEventListener('mousemove', handleMouseMove);
        };
    });
</script>

<div class="container">
    <div class="background-noise"></div>
    <SplatterSVG />

    <div class="top-triangle" bind:this={topTriangle}></div>
    <div class="bottom-triangle" bind:this={bottomTriangle}></div>
</div>

<style>

    .container {
        position: absolute;
        width: 100%;
        height: 100%;
        overflow: clip;
    }

    .top-triangle, .bottom-triangle{
        position: absolute;
        width: 20rem;
        aspect-ratio: 1/cos(30deg);
        opacity: 50%;
        z-index: -1;
        display: none;
        background: #F9B3FF;
        transition: transform 0.3s ease-out; /* Smooth movement */
    }

    @media (min-width: 900px){
        .top-triangle {
            clip-path: polygon(50% 100%,100% 0,0 0);
            top: 0;
            right: -5vw;
            display: block;
        }
    }

    @media (min-width: 900px){
        .bottom-triangle {
            clip-path: polygon(50% 0,100% 100%,0 100%);
            bottom: 0;
            left: -5vw;
            display: block;
        }
    }
    .background-noise{
        position: fixed;
        top: -50%;
        left: -50%;
        right: -50%;
        bottom: -50%;
        width: 200%;
        height: 200%;
        background: transparent url('http://assets.iceable.com/img/noise-transparent.png') repeat 0 0;
        background-repeat: repeat;
        opacity: .9;
        z-index: 100;
        pointer-events: none;
    }

</style>