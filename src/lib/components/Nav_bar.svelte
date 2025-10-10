<nav>
    <a href="/" class="about-me">About me</a>
    <a href="/blog" class="blog">Blog</a>
    <a href="/experiments" class="experiments">Experiments</a>
</nav>

<style>

    nav {
        display: flex;
        flex-direction: column;   
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
        opacity: 70%;
        &:hover{
            color: var(--main-accent-color);
            opacity: 100%;
        }
    }
</style>