<script>
  // Koppelen van de button via bind:this zodat we hem in JS kunnen aanspreken
  let button;

  // EFFECT SVELTEKIT: https://svelte.dev/docs/svelte/$effect
  $effect(() => {

    let fade_out_time = parseInt(getComputedStyle(document.documentElement).getPropertyValue('--fade-out-time'), 10); // Is hetzelfde als de variable in de stylesheet, de 10 betekent decimals: Jad
    // ParseInt: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt
    // Aanspreken van css: https://stackoverflow.com/questions/36088655/accessing-a-css-custom-property-aka-css-variable-through-javascript

    //Geeft een lege array mee gelijk aan het aantal, het aantal word via de random functie aangesproken bij 'dots'
    function dots(amount) {
      return Array.from({ length: amount });
    }

    //Maakt een functie aan met een min en een max, de min en max worden later bepaald bij de const angle, en, const distance. Gemaakt in: https://codepen.io/Lutrian1/pen/jEPNJMe?editors=1111
    function random(min, max) {
      return Math.random() * (max - min) + min;
    }

    // Wanneer button wordt geklikt, voer dit uit.
    const handleClick = (event) => {
      const particles = [];

      // Voor elke particle (deze staat dus random tussen 5 en 10), voer onderstaande code uit
      dots(random(5, 10)).forEach(() => {
        // Maken van een span, en deze de particle-animations class meegeven
        const particle = document.createElement('span');
        // Add a unique class so it’s easier to target (voeg een unieke class toe, dit moet een :global class zijn, Sveltekit doet ander stom bij het maken van een SPAN)
        particle.classList.add('particle-animations', 'particle');

        // Toevoegen van random angle en distance in css
        const angle = random(0, 360);
        const distance = random(70, 100);

        particle.style.setProperty('--angle', angle + 'deg');
        particle.style.setProperty('--distance', distance + 'px');

        // Geen idee, was van joshwcomeau zijn course lol
        button.appendChild(particle);
        particles.push(particle);
      });

      // Verwijderen van elke particle na de fade_out_time + wat extra zodat dit altijd smooth is
      setTimeout(() => {
        particles.forEach((particle) => {
          particle.remove();
        });
      }, fade_out_time + 200);
    };

    button.addEventListener('click', handleClick);

    // Cleanup functie (zoals onDestroy)
    return () => {
      button.removeEventListener('click', handleClick);
    };
  });
</script>

<main>
  <button bind:this={button}>Click me</button>
  <a href="https://codepen.io/Lutrian1/pen/gbPGRJq">Codepen</a>
</main>

<style>
  :root {
    --fade-out-time: 500ms;
  }

  main {
    width: 100%;
    height: 100%;
    position: fixed;
    margin: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  button {
    width: 15vw;
    min-width: 150px;
    height: 7vh;
    min-height: 70px;
    background: var(--main-accent-color);
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 1.2rem;
    cursor: pointer;
    position: relative;
    transition: transform 0.1s;
  }

  button:active {
    transform: scale(0.95);
  }

  @keyframes fadeToTransparent {
    from {
      opacity: 1;
    }
    to {
      opacity: 0;
    }
  }

  @keyframes disperse {
    to {
      transform: translate(
        calc(cos(var(--angle)) * var(--distance)),
        calc(sin(var(--angle)) * var(--distance))
      );
    }
  }


  /* orgineel is dit een span maar voor sveltekit moet dit dus een class zijn */
  :global(.particle) {
    position: absolute;
    width: 10px;
    height: 10px;
    background: var(--main-color, #fff);
    border-radius: 50%;
    pointer-events: none;
    left: 50%;
    top: 50%;
    opacity: 1;
  }

  :global(.particle-animations) {
    animation:
      fadeToTransparent var(--fade-out-time) forwards,
      disperse var(--fade-out-time) forwards ease-out;
  }
</style>