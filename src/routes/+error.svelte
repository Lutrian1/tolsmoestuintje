<script>
	import { page } from '$app/state';
  import { Background } from '$lib';
  import { Main_heading } from '$lib';

</script>

<header>
  <h1>Oops, a <strong>404 {page.error.message}</strong></h1>
  <p>We couldn't find the page you were looking for. Navigate back to the homepage.</p>

  <a href="/">Home</a>
</header>

<main>
  <Background />
</main>

<style>

header{
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  z-index: 5000;
}

main{
  opacity: 40%;
}

h1{
  font-size: var(--heading-1);
  margin: 0 0 1rem 0;
  strong{
    color: var(--main-accent-color);
  }
}

p{
  font-size: var(--heading-3);
  margin: 0 0 1rem 0;
  text-align: center;
}

a{
  font-size: var(--heading-3);
}


</style>