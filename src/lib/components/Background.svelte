<script>
    import { SplatterSVG } from '$lib';
</script>

<div class="background-noise"></div>

<SplatterSVG />

<div class="top-triangle"></div>
<div class="bottom-triangle"></div>

<style>

    .top-triangle, .bottom-triangle{
        position: absolute;
        width: 20rem;
        aspect-ratio: 1/cos(30deg);
        opacity: 50%;
        z-index: -1;
        @media (min-width: 900px){
            background: #F9B3FF;
        }
    }

    @media (min-width: 900px){
        .top-triangle {
            clip-path: polygon(50% 100%,100% 0,0 0);
            top: 0;
            right: 0;
        }
    }

    @media (min-width: 900px){
        .bottom-triangle {
            clip-path: polygon(50% 0,100% 100%,0 100%);
            bottom: 0;
        }
    }
    .background-noise{
        position: fixed;
        top: -50%;
        left: -50%;
        right: -50%;
        bottom: -50%;
        width: 200%;
        height: 200%;
        background: transparent url('http://assets.iceable.com/img/noise-transparent.png') repeat 0 0;
        background-repeat: repeat;
        opacity: .9;
        z-index: 100;
        pointer-events: none;
    }

</style>