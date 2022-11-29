<script lang="ts">
	import { PlayOutline } from "carbon-icons-svelte";
    import { inview } from 'svelte-inview';
	import { fade } from "svelte/transition";

    let isInView: boolean;
 
</script>

<section id="hero"
use:inview={{ unobserveOnEnter: true, rootMargin: '0%' }}
on:change={({ detail }) => {
    isInView = detail.inView;
}}>
  {#if isInView}
    <div class="hero-container"
    in:fade={{duration:1500}}>
        <div class="caption">
            <h2>Welcome at
                <br>
                <span>PHUHUYENTECH.CO</span>
            </h2>
            <h3>Our business is helping you grow your business</h3>
            <p>Top Web & Applications Solutions</p>
            <div class="hero-button">
                <a href="#about" class="btn-get-started">Get started</a>
                <a href="" class="btn-watch-video">
                    <i><PlayOutline size={32}/></i>
                    <span>Watch Video</span>
                </a>
            </div>
        </div>
    </div>
    {/if}
</section>
<style lang="scss">
@use 'src/variables';
#hero {
    width: 100%;
    position: relative;
    background: url(../images/hero-bg.jpeg) center center;
    background-size: cover;
    padding: 90px 0 0 0;
    height: 100vh;
}
.hero-container {
    position: relative;
}
.caption {
    height: 80vh;
    text-align: center;
    align-items: center;
    justify-content: center;
    display: flex;
    flex-direction: column;
    h2 {
        font-size: 80px;
        font-weight: 700;
        margin-bottom: 20px;
        color: #1b2e35;
        text-transform: uppercase;
        span {
            color: #30ba15;
        }
    }
    h3 {
        margin-top: 0;
        margin-bottom: 8px;
        font-weight: 500;
        line-height: 1.2;
    }
    p {
        color: rgb(92 92 92 / 80%);
        font-weight: 400;
        margin-bottom: 30px;
        margin-top: 0;
    }
}
.hero-button {
    display: flex;
    text-align: center;
    .btn-get-started {
        font-size: 14px;
        font-weight: 500;
        letter-spacing: 1px;
        display: inline-block;
        padding: 14px 40px;
        border-radius: 50px;
        transition: 0.3s;
        color: #30ba15;
        background: rgba(255, 255, 255, 0.1);
        box-shadow: 0 0 15px rgb(0 0 0 / 8%);
        text-decoration: none;
    }
    .btn-watch-video {
        display: flex;
        font-size: 14px;
        margin-left: 25px;
        color: #30ba15;
        font-weight: 600;
        align-items: center;
        text-decoration: none;
        i {
            color: #30ba15;
            font-size: 32px;
            line-height: 0;
            margin-right: 8px;
        }
    }
}
</style>