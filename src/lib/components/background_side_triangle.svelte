<script>
    import { SplatterSVG } from '$lib';
    
    let leftTriangle;

    $effect(() => {

        const handleMouseMove = (e) => {
            const mouseY = e.clientY;
            const windowHeight = window.innerHeight;
            const normalizedY = mouseY / windowHeight;

            // Move the triangle up/down slightly based on mouse
            const moveY = (normalizedY - 0.5) * 400; // 200px max movement
            leftTriangle.style.transform = `translateY(calc(-50% + ${moveY}px))`;
        };

        document.addEventListener('mousemove', handleMouseMove);

	});
</script>

<div class="left-triangle" bind:this={leftTriangle}></div>

<div class="background-noise"></div>
<SplatterSVG />

<style>

    .left-triangle {
        position: fixed;
        top: 50%;
        left: 0;
        width: 13rem;
        aspect-ratio: 1 / cos(30deg);
        background: #f9b3ff;
        opacity: 0.5;
        clip-path: polygon(0 0,100% 50%,0 100%);
        transform: translateY(-50%);
        transition: transform 0.3s ease-out;
        z-index: -1;
    }

    
	.background-noise {
		position: fixed;
		top: -50%;
		left: -50%;
		right: -50%;
		bottom: -50%;
		width: 200%;
		height: 200%;
		background: transparent url('http://assets.iceable.com/img/noise-transparent.png') repeat 0 0;
		opacity: 0.9;
		z-index: 100;
		pointer-events: none;
	}

</style>