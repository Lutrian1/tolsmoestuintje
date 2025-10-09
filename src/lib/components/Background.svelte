<div class="background-noise"></div>

<div class="top-triangle"></div>
<div class="bottom-triangle"></div>

<style>

    @media (min-width: 1100px){
        .top-triangle {
            position: absolute;
            width: 20rem;
            aspect-ratio: 1/cos(30deg);
            clip-path: polygon(50% 100%,100% 0,0 0);
            background: #F9B3FF;
            opacity: 50%;
            top: 0;
            right: 0;
        }
    }

    @media (min-width: 1100px){
        .bottom-triangle {
            position: absolute;
            width: 20rem;
            aspect-ratio: 1/cos(30deg);
            clip-path: polygon(50% 0,100% 100%,0 100%);
            background: #F9B3FF;
            opacity: 50%;
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