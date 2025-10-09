<aside>

    <p class="copyright">Made by Luuk Tol, 2025</p>
          
</aside>

<h2> Luuk <span>Tol.</span></h2>

<p class="about-me">Hello there! My name is Luuk Tol, and I'm a Front-End Development student at the HVA (University of Applied Sciences Amsterdam). 
This site is my Digital Garden—a personal space where you can see all my goofs and probably not great code, but atleast I learned something from it. 
It's my collection of experiments, a playground where I tinker with code, explore new technologies, and push my creative boundaries. 
So please, scroll around, and see what I have been working on, and hopefully you learn something new too.</p>

<style>
    .copyright{
        position: absolute;
        font-size: 0.9rem;
        top: -1.1rem;
        width: 8rem;
        margin: 0;
        opacity: 80%;
    }

    aside{
        position: absolute;
    }

    h2{
        font-size: var(--heading-2);
        position: relative;
        max-width: 15rem;
        margin: 0;
          text-shadow: 
            2px   0  0   #000, 
            -2px   0  0   #000, 
            0    2px 0   #000, 
            0   -2px 0   #000, 
            1px  1px 0   #000, 
            -1px -1px 0   #000, 
            1px -1px 0   #000, 
            -1px  1px 0   #000,
            1px  1px 5px #000;
        span{
            color: var(--main-accent-color);
        }
    }

    .about-me{
        font-size: clamp(0.7rem, 3vw, 1.75rem);
        margin: 0;
        position: relative;
        display: flex;
        align-items: center;
        &::before{
            border-left: 2px solid black;
            content: "";
            display: block;
            height: 10rem;
            left: -2rem;
            position: absolute;
            width: 1px;
            z-index: 0;
        }
    }

    @container footer (width < 65.625rem) {
        .about-me{
            max-width: 45rem;
            font-size: clamp(0.7rem, 3vw, 1.5rem);
        }
    }
</style>