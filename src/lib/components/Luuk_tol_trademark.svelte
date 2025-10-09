<aside>

    <p class="copyright">Made by Luuk Tol, 2025</p>
          
</aside>

<h2> Luuk <span>Tol.</span></h2>

<p class="about-me">Hello there! My name is Luuk Tol, and I'm a Front-End Development student at the HVA (University of Applied Sciences Amsterdam). 
This site is my Digital Garden—a personal space on the web where I plant the seeds of new ideas and watch them grow. 
It's a living collection of experiments, a playground where I tinker with code, explore new technologies, and push my creative boundaries. 
Each project you'll find here is a step in my journey to hone my skills and become a better front-end developer.</p>

<style>
    .copyright{
        font-size: 0.9rem;
    }

    aside{
        position: absolute;
    }

    h2{
        font-size: var(--heading-2);
        position: relative;
        max-width: 20rem;
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
</style>