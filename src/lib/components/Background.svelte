<script>
	import { onMount } from 'svelte';
	import { SplatterSVG } from '$lib';

	let topTriangle;
	let bottomTriangle;
	let canvas;

	let isPainting = false;

	let context;
	let width, height;
	let lastX = null;
	let lastY = null;
	const brushColor = { r: 187, g: 87, b: 196 }; // #BB57C4 in RGB
	let baseBrushSize;

	onMount(() => {
		// =======================
		// Triangle Follow Code
		// =======================
		const handleMouseMove = (e) => {
			if (!topTriangle || !bottomTriangle) return;

			const mouseX = e.clientX;
			const windowWidth = window.innerWidth;
			const moveAmount = 500;
			const normalizedX = mouseX / windowWidth;

			const topMoveX = -normalizedX * moveAmount;
			const bottomMoveX = normalizedX * moveAmount;

			topTriangle.style.transform = `translateX(${topMoveX}px)`;
			bottomTriangle.style.transform = `translateX(${bottomMoveX}px)`;
		};

		document.addEventListener('mousemove', handleMouseMove);

		// =======================
		// Only run on desktop
		// =======================
		if (window.innerWidth > 768) {
			context = canvas.getContext('2d');
			width = window.innerWidth;
			height = window.innerHeight;

			canvas.width = width;
			canvas.height = height;

			// =======================
			// Canvas Click: Toggle Painting Mode
			// =======================
			const handleClick = (e) => {
				isPainting = !isPainting;

				if (isPainting) {
					baseBrushSize = getRandomSize(); // Get a new brush size
					lastX = null;
					lastY = null;
					canvas.classList.remove('hidden');
				} else {
					context.clearRect(0, 0, canvas.width, canvas.height); // Clear canvas
					canvas.classList.add('hidden');
					lastX = null;
					lastY = null;
				}
			};

			// =======================
			// Mouse Move: Draw Line If Painting Is Enabled
			// =======================
			const handleDraw = (e) => {
				if (!isPainting) return;

				const x = e.clientX;
				const y = e.clientY;

				if (lastX === null || lastY === null) {
					lastX = x;
					lastY = y;
					return;
				}

				const opacity = 0.8 + Math.random() * 0.7;
				const sizeVariation = Math.random() * 4 - 2;
				const brushSize = Math.max(2, baseBrushSize + sizeVariation);

				context.strokeStyle = `rgba(${brushColor.r}, ${brushColor.g}, ${brushColor.b}, ${opacity.toFixed(2)})`;
				context.lineWidth = brushSize;
				context.lineCap = 'round';
				context.lineJoin = 'round';

				context.beginPath();
				context.moveTo(lastX, lastY);
				context.lineTo(x, y);
				context.stroke();
				context.closePath();

				// Optional splatter effect
				if (Math.random() < 0.1) {
					drawSplatter(x, y);
				}

				lastX = x;
				lastY = y;
			};

			// =======================
			// Helpers: Random Brush Size
			// =======================
			function getRandomSize() {
				return Math.floor(Math.random() * 15) + 5;
			}

			// =======================
			// Splatter Drawing Function
			// =======================
			function drawSplatter(x, y) {
				const dots = Math.floor(Math.random() * 5) + 3;

				for (let i = 0; i < dots; i++) {
					const angle = Math.random() * Math.PI * 2;
					const distance = Math.random() * 30 + 5;
					const dotX = x + Math.cos(angle) * distance;
					const dotY = y + Math.sin(angle) * distance;
					const dotSize = Math.random() * 3 + 1;
					const opacity = Math.random() * 0.5 + 0.2;

					context.beginPath();
					context.arc(dotX, dotY, dotSize, 0, Math.PI * 2);
					context.fillStyle = `rgba(${brushColor.r}, ${brushColor.g}, ${brushColor.b}, ${opacity.toFixed(2)})`;
					context.fill();
					context.closePath();
				}
			}

			// Reset last position on mouse leave
			const handleMouseLeave = () => {
				lastX = null;
				lastY = null;
			};

			document.addEventListener('click', handleClick);
			document.addEventListener('mousemove', handleDraw);
			canvas.addEventListener('mouseleave', handleMouseLeave);

			// Cleanup
			return () => {
				document.removeEventListener('mousemove', handleMouseMove);
				document.removeEventListener('click', handleClick);
				document.removeEventListener('mousemove', handleDraw);
				canvas.removeEventListener('mouseleave', handleMouseLeave);
			};
		}
	});
</script>


<div class="container">
	<div class="background-noise"></div>
	<SplatterSVG />

	<div class="top-triangle" bind:this={topTriangle}></div>
	<div class="bottom-triangle" bind:this={bottomTriangle}></div>
</div>

<canvas bind:this={canvas} class="hidden"></canvas>

<style>
	.container {
		position: absolute;
		width: 100%;
		height: 100%;
		overflow: clip;
	}

	.top-triangle,
	.bottom-triangle {
		position: absolute;
		width: 20rem;
		aspect-ratio: 1 / cos(30deg);
		opacity: 50%;
		z-index: -1;
		display: none;
		background: #f9b3ff;
		transition: transform 0.3s ease-out;
	}

	@media (min-width: 950px) {
		.top-triangle {
			clip-path: polygon(50% 100%, 100% 0, 0 0);
			top: 0;
			right: -5vw;
			display: block;
		}

		.bottom-triangle {
			clip-path: polygon(50% 0, 100% 100%, 0 100%);
			bottom: 0;
			left: -5vw;
			display: block;
		}
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
		background-repeat: repeat;
		opacity: 0.9;
		z-index: 100;
		pointer-events: none;
	}

	canvas {
		position: fixed;
		top: 0;
		left: 0;
		z-index: 1000;
		width: 100%;
		height: 100%;
		pointer-events: none;
	}

	/* SUPER IMPORTANT, THIS CLASS HIDES THE CANVAS */

	.hidden {
		display: none;
	}

</style>
