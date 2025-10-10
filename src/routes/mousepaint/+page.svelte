<script>

</script>

<main>
    <h1>Click to paint</h1>
    <canvas>

    </canvas>
</main>

<style>
    
    h1{
       font-size: var(--heading-1); 
       opacity: 50%;
       pointer-events: none;
    }
    main{
        width: 100%;
        height: 100%;
        position: fixed;
        margin: 0;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    canvas{
        position: fixed;
		top: 0;
		left: 0;
		z-index: 1000;
		width: 100%;
		height: 100%;
		pointer-events: none;
    }
</style>