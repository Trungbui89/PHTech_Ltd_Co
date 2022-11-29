<script lang="ts">
    import { fade, fly, scale } from "svelte/transition";
    import { inview } from 'svelte-inview';
    
    let isInView: boolean;
    
</script>
<section id="contact-us"
use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
on:change={({ detail }) => {
    isInView = detail.inView;
}}>
    {#if isInView}
        <div class="contact-us-content">
            <header class="contact-us-header"
            in:scale="{{duration: 1500, start: 1.5, opacity: 0}}">
                <h2>Read to start something great?</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
                <a href="mailto:abcd@gmail.com" class="contact-us-button">Contact Us</a>
            </header>
        </div>
    {/if}
</section>

<style lang="scss">
@use 'src/variables';
#contact-us {
    background: linear-gradient(rgb(7 7 7 / 60%), rgb(0 0 0 / 60%)), url(/images/background2.jpeg) center center;
    background-size: cover;
    padding: 150px 60px;
    border-radius: 0px;
    overflow: hidden;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center;
}
.contact-us-content {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
}
.contact-us-header {
    text-align: center;
    padding-bottom: 60px;
    h2 {    
        font-size: 32px;
        font-weight: 600;
        margin-bottom: 20px;
        position: relative;
        color: #fff
    }
    p {
        margin-bottom: 0;
        display: block;
        margin-block-start: 1em;
        margin-block-end: 1em;
        margin-inline-start: 0px;
        margin-inline-end: 0px;
        color: #fff
    }
}
.contact-us-button {
    font-weight: 500;
    font-size: 16px;
    letter-spacing: 1px;
    display: inline-block;
    padding: 12px 48px;
    border-radius: 50px;
    transition: 0.5s;
    margin: 10px;
    border: 2px solid #fff;
    color: #fff;
    text-decoration: none;
    transition: all 0.3s ease-in-out;
}
.contact-us-button:hover {
    background-color: #30ba15;
}
</style>