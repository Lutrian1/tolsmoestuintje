<nav>
    <a href="/" class="about-me">About me</a>
    <a href="/blog" class="blog">Blog</a>
    <a href="/experiments" class="experiments">Experiments</a>
</nav>

<style>

    nav {
        display: flex;
        flex-direction: column;   
        text-align: center;
        gap: 0.2rem;
    }

    @container header (min-width: 28.125rem) {
        nav {
            flex-direction: row;
            justify-content: space-around;
        }
    }

    a{
        color: var(--main-color);
        font-size: clamp(3rem, 4vw, 7rem);
        text-decoration: none;
        background-color: var(--secondary-accent-color);
        border: solid 2px var(--main-accent-color);
    }

    @container header (min-width: 28.125rem) {
        a{
            color: var(--main-color);
            background-color: transparent;
            border: none;
            opacity: 70%;
            &:hover{
                color: var(--main-accent-color);
                opacity: 100%;
            }
        }
    }
</style>