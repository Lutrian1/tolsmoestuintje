<script>
	import { onMount } from 'svelte';
	import { SplatterSVG } from '$lib';

	let topTriangle;
	let bottomTriangle;
	let canvas;

	let isPainting = false;

	let context;
	let width, height;
	let startPos, prevPos, dist;
	const colour = '#BB57C4';

	onMount(() => {
		// Triangle hover movement
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

		// Canvas setup
		context = canvas.getContext('2d');
		width = window.innerWidth;
		height = window.innerHeight;

		canvas.width = width;
		canvas.height = height;

		startPos = { x: width / 2, y: height / 2 };
		prevPos = { x: width / 2, y: 0 };
		dist = { x: 0, y: 0 };

		// Painting logic
		const mouseMove = (e) => {
			if (!isPainting) return;

			const distance = Math.sqrt(
				Math.pow(prevPos.x - startPos.x, 2) +
				Math.pow(prevPos.y - startPos.y, 2)
			);

			const a = distance * 10 * (Math.pow(Math.random(), 2) - 0.5);
			const r = Math.random() - 0.5;
			const size = (Math.random() * 15) / distance;

			dist.x = (prevPos.x - startPos.x) * Math.sin(0.5) + startPos.x;
			dist.y = (prevPos.y - startPos.y) * Math.cos(0.5) + startPos.y;

			startPos.x = prevPos.x;
			startPos.y = prevPos.y;

			prevPos.x = e.clientX;
			prevPos.y = e.clientY;

			const lWidth =
				(Math.random() + 2 - 0.5) * size +
				(1 - Math.random() + 1.5 - 0.5) * size;

			context.lineWidth = lWidth;
			context.lineCap = 'round';
			context.lineJoin = 'round';

			context.beginPath();
			context.moveTo(startPos.x, startPos.y);
			context.quadraticCurveTo(dist.x, dist.y, prevPos.x, prevPos.y);

			context.fillStyle = colour;
			context.strokeStyle = colour;

			context.moveTo(startPos.x + a, startPos.y + a);
			context.lineTo(startPos.x + r + a, startPos.y + r + a);

			context.stroke();
			context.fill();
			context.closePath();
		};

		const handleClick = (e) => {
			isPainting = !isPainting;

			if (isPainting) {
				startPos = { x: e.clientX, y: e.clientY };
				prevPos = { x: e.clientX, y: e.clientY };
				canvas.classList.remove('hidden');
			} else {
				canvas.classList.add('hidden');
			}
		};

		const handleDoubleClick = (e) => {
			e.preventDefault();
			context.clearRect(0, 0, width, height);
			isPainting = false;
			canvas.classList.add('hidden');
		};

		document.addEventListener('mousemove', mouseMove);
		document.addEventListener('click', handleClick);
		document.addEventListener('dblclick', handleDoubleClick);

		return () => {
			document.removeEventListener('mousemove', handleMouseMove);
			document.removeEventListener('mousemove', mouseMove);
			document.removeEventListener('click', handleClick);
			document.removeEventListener('dblclick', handleDoubleClick);
		};
	});
</script>

<div class="container">
	<div class="background-noise"></div>
	<SplatterSVG />

	<div class="top-triangle" bind:this={topTriangle}></div>
	<div class="bottom-triangle" bind:this={bottomTriangle}></div>
</div>

<canvas bind:this={canvas} id="canvas" class="hidden"></canvas>

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

	.hidden {
		display: none;
	}
</style>
