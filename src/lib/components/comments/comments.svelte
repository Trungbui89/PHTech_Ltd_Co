<script lang="ts">
    import { fade, fly } from "svelte/transition";
    import { Quotes, StarFilled } from 'carbon-icons-svelte'
    import { Splide, SplideSlide } from '@splidejs/svelte-splide';
    import { inview } from 'svelte-inview';
    import '@splidejs/svelte-splide/css';

    let commentsInfo = [
        {src: '/images/Keena Lara.jpeg', name: 'Keena Lara', office: 'Store Owner', quote: "Enim nisi quem export duis labore cillum quae magna enim sint quorum nulla quem veniam duis minimtempor labore quem eram duis noster aute amet eram fore quis minim."},
        {src: '/images/Afa Rose.jpeg', name: 'Afa Rose', office: 'Web Designer', quote: "Enim nisi quem export duis labore cillum quae magna enim sint quorum nulla quem veniam duis minimtempor labore quem eram duis noster aute amet eram fore quis minim."},
        {src: '/images/Jhone Doe.jpeg', name: 'Jhone Doe', office: 'CFO', quote: "Proin iaculis purus consequat sem cure digni ssim donec porttitora entum suscipit rhoncus.Accusantium quam, ultricies eget id, aliquam eget nibh et. Maecen aliquam."},
        {src: '/images/Fizzi Brandon.jpeg', name: 'Fizzi Brandon', office: 'Freelancer', quote: "Enim nisi quem export duis labore cillum quae magna enim sint quorum nulla quem veniam duis minimtempor labore quem eram duis noster aute amet eram fore quis minim."},
        {src: '/images/Jhone Doe.jpeg', name: 'Jhone Doe', office: 'CFO', quote: "Proin iaculis purus consequat sem cure digni ssim donec porttitora entum suscipit rhoncus.Accusantium quam, ultricies eget id, aliquam eget nibh et. Maecen aliquam."},
        {src: '/images/Keena Lara.jpeg', name: 'Keena Lara', office: 'Store Owner', quote: "Enim nisi quem export duis labore cillum quae magna enim sint quorum nulla quem veniam duis minimtempor labore quem eram duis noster aute amet eram fore quis minim."}
    ]
    let isInView: boolean;
    let isInView1: boolean;
    

</script>
<section id="comments">
    <div class="comments-content"
    >
        <header class="comments__header"
        use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
        on:change={({ detail }) => {
            isInView = detail.inView;
        }}>
            {#if isInView}
            <div class="header-title"
            in:fly="{{ y: 100, duration: 1500 }}">
                <h2>Testimonials</h2>
                <p>Our business is helping you grow your business</p>
            </div>
            {/if}
        </header>
        <div class="comments__slide"
        use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
        on:change={({ detail }) => {
            isInView1 = detail.inView;
        }}>
        {#if isInView1}
            <div class="swiper-wraper"
            in:fly="{{ y: 100, duration: 1500, opacity: 0 }}">
                <Splide 
                aria-label="Top Favorite Comments" 
                options={{
                    width:'90%',
                    rewind: true,
                    autoplay: true,
                    speed: 2000,
                    rewindSpeed: 2000
                    }}>
                    {#each commentsInfo as commentsItem}
                        <SplideSlide>
                            <div class="swiper-slide">
                                <div class="comments-wrap">
                                    <div class="comments-item">
                                        <div class="info-box">
                                            <img src="{commentsItem.src}" alt="" class="comments-info-img">
                                            <div class="comments-info">
                                                <h3>{commentsItem.name}</h3>
                                                <h4>{commentsItem.office}</h4>
                                                <div class="star">
                                                    <StarFilled class="star-fill"/>
                                                    <StarFilled class="star-fill"/>
                                                    <StarFilled class="star-fill"/>
                                                    <StarFilled class="star-fill"/>
                                                    <StarFilled class="star-fill"/>
                                                </div>
                                            </div>
                                        </div>
                                        <p>
                                            <i class="quote quote-icon-left"><Quotes/></i>
                                            "{commentsItem.quote}"
                                            <i class="quote quote-icon-right"><Quotes/></i>
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </SplideSlide>
                        <div class="splide__arrows"></div>
                        <div class="splide__pagination__page"></div>
                    {/each}
                </Splide>
            </div>
            {/if}
        </div>     
    </div>
</section>

<style lang="scss">
@use 'src/variables';
.comments-content {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
    padding: 90px 0;
    overflow: hidden;
    .comments__header {
        text-align: center;
        padding-bottom: 60px;
        h2 {    
            font-size: 32px;
            font-weight: 600;
            margin-bottom: 20px;
            position: relative;
        }
        p {
            margin-bottom: 0;
            display: block;
            margin-block-start: 1em;
            margin-block-end: 1em;
            margin-inline-start: 0px;
            margin-inline-end: 0px;
            color: #6f6f6f;
        }
    }
    .comments__slide {
        .swiper-wraper {
            visibility: hidden;
            position: relative;
            width: 100%;
            height: 100%;
            z-index: 1;
            display: flex;  
            box-sizing: content-box;
            list-style: none;
            justify-content: center;   
            .swiper-slide {
                flex-shrink: 0;
                width: 100%;
                height: 100%;
                position: relative;   
                .comments-wrap {
                    padding-left: 10px;  
                    .comments-item {
                        box-sizing: content-box;
                        padding: 95px 40px;
                        margin: 30px 10px;
                        box-shadow: 0 0 2px 0 rgb(255 39 7 / 28%);
                        position: relative;
                        background: #fff;
                        display: flex;
                        p {
                            font-style: italic;
                            margin: 15px auto 15px auto;
                            .quote-icon-left {
                                display: inline-block;
                                left: -5px;
                                position: relative;
                                color: #30ba15;
                                font-size: 26px;
                                line-height: 0;
                            }
                            .quote-icon-right {
                                padding-top: 12px;
                                display: inline-block;
                                right: -5px;
                                position: relative;
                                top: 10px;
                                transform: scale(-1, 1);
                                transform: rotate(180deg);
                                color: #30ba15;
                                font-size: 26px;
                                line-height: 0;
                            }
                        } 
                        .info-box {
                            min-width: 276px;
                            align-items: center;
                            display: flex;
                            .comments-info-img {
                                width: 90px;
                                border-radius: 50px;
                                margin-right: 15px;
                                flex-shrink: 0;
                                vertical-align: middle;
                            }   
                            .comments-info {
                                h3 {
                                    font-size: 18px;
                                    font-weight: bold;
                                    margin: 10px 0 5px 0;
                                    color: #000;
                                }
                                h4 {
                                    font-size: 14px;
                                    color: #999;
                                    margin: 0;
                                }   
                                .star {
                                    color: #f7c633;
                                    margin: 10px 0;
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
.splide__arrows {
display: none;
}
.splide__pagination__page {
    &:is(.is-active) {
        background-color: #30ba15;
        transform: scale(1.4);
        z-index: 1;
    }
}
</style>