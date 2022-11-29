<script lang="ts">
    import { scale } from "svelte/transition";
    import { Splide, SplideSlide } from '@splidejs/svelte-splide';
    import '@splidejs/svelte-splide/css';
    import { inview } from 'svelte-inview';

    let clientsInfo = [
        {src: '/images/client-1.png'},
        {src: '/images/client-2.png'},
        {src: '/images/client-3.png'},
        {src: '/images/client-4.png'},
        {src: '/images/client-5.png'},
        {src: '/images/client-6.png'},
        {src: '/images/client-7.png'},
        {src: '/images/client-8.png'}
    ]
    let isInView: boolean;

</script>
<section id="clients"
use:inview={{ unobserveOnEnter: true, rootMargin: '0%' }}
on:change={({ detail }) => {
    isInView = detail.inView;
}}>
    {#if isInView}
    <div class="clients-content">
        <div class="clients-container"
        in:scale="{{duration: 1500, start: 1.5, opacity: 0}}">
            <div class="clients-wraper">
            <Splide
            aria-label="Top Favorite Comments"
            options={{
                rewind: true,
                autoplay: true,
                perPage: 5,
                perMove: 1,
                speed: 2000,
                rewindSpeed: 2000
            }}>
                {#each clientsInfo as client}
                <SplideSlide>
                    <div class="client-logo">
                        <img src={client.src} alt="">
                    </div>        
                </SplideSlide>
                {/each}
                <div class="splide__arrows"></div>
                <div class="splide__pagination"></div>
            </Splide>   
            </div>
        </div>
    </div>
    {/if}
</section>
<style lang="scss">
    @use 'src/variables';
#clients {
    background-color: rgb(239 239 239 / 30%);
    padding: 40px 0;
}
.clients-content {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
}
.clients-container {
    max-width: 99rem;
    width: 89%;
    margin-left: auto;
    margin-right: auto;
    position: relative;
    overflow: hidden;
    list-style: none;
    padding: 0;
    z-index: 1;
}
.clients-wraper {
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 1;
    display: flex;
    box-sizing: content-box;
    justify-content: center;
}
:is(.client-logo) {
    width: 100%;
    margin-right: 120px;
    position: relative;
    padding: 0 16px;
    img {
        max-width: 100%;
        width: auto;
        height: auto;
        vertical-align: middle;
    }

}
.splide__arrows, .splide__pagination {
    display: none;
}
</style>