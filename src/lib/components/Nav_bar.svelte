<nav>
    <a href="/" class="about-me">About me</a>
    <a href="/blog" class="blog">Blog</a>
    <a href="/experiments" class="experiments">Experiments</a>
</nav>

<style>
    nav{
        display: flex;
        justify-content: space-around;
    }
    a{
        color: var(--main-color);
        font-size: clamp(2rem, 4vw, 7rem);
        text-decoration: none;
        opacity: 70%;
        &:hover{
            color: var(--main-accent-color);
            opacity: 100%;
        }
    }
</style>