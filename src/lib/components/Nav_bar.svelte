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
        gap: 0.5rem;
    }

    @container header (min-width: 28.125rem) {
        nav {
            flex-direction: row;
            justify-content: space-around;
            gap: 0;
        }
    }

    a{
        color: var(--main-color);
        opacity: 80%;
        font-size: clamp(3rem, 4vw, 7rem);
        text-decoration: none;
        background: linear-gradient(white 60%, var(--secondary-accent-color));
        border-bottom: solid 2px var(--main-accent-color);
    }

    @container header (min-width: 28.125rem) {
        a{
            color: var(--main-color);
            border-bottom: none;
            background: transparent;
            opacity: 70%;
            &:hover{
                color: var(--main-accent-color);
                opacity: 100%;
            }
        }
    }
</style>