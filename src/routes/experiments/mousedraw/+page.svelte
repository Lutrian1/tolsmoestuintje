<script>
  let canvas;

  $effect(() => {
    const context = canvas.getContext("2d");

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let lastX = null;
    let lastY = null;

    const handleMouseMove = (event) => {
      const xPos = event.clientX;
      const yPos = event.clientY;

      if (lastX === null || lastY === null) {
        lastX = xPos;
        lastY = yPos;
        return;
      }

      context.beginPath();
      context.moveTo(lastX, lastY);
      context.lineTo(xPos, yPos);
      context.strokeStyle = "#000";
      context.lineWidth = 2;
      context.stroke();
      context.closePath();

      lastX = xPos;
      lastY = yPos;
    };

    const handleMouseLeave = () => {
      lastX = null;
      lastY = null;
    };

    canvas.addEventListener("mousemove", handleMouseMove);
    canvas.addEventListener("mouseleave", handleMouseLeave);

    return () => {
      canvas.removeEventListener("mousemove", handleMouseMove);
      canvas.removeEventListener("mouseleave", handleMouseLeave);
    };
  });
</script>

<div class="block">

  <main>
    <h1>Hover here</h1>
    <canvas bind:this={canvas} style="display: block;"></canvas>
  </main>

</div>

<style>
  h1 {
    font-size: 64px;
    opacity: 50%;
    pointer-events: none;
  }

  main {
    width: 100%;
    height: 100%;
    position: fixed;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    width: 100%;
    height: 100%;
  }
</style>
