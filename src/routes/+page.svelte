<script lang="ts">

    import OurTeam from '$lib/components/ourteam/ourteam.svelte';
    import ContactUsForm from '$lib/components/contactUsForm/contactUsForm.svelte';
    import About from '$lib/components/aboutUs/aboutUs.svelte'
    import WhyUs from '$lib/components/whyUs/whyUs.svelte'
    import Comments from '$lib/components/comments/comments.svelte'
    import Posts from '$lib/components/posts/posts.svelte'
    import ContactUs from '$lib/components/contactUs/contactUs.svelte'
    import Clients from '$lib/components/clients/clients.svelte'
    import Footer from '$lib/components/footer/footer.svelte'
    import Hero from '$lib/components/Hero/hero.svelte'
    import Services from '$lib/components/services/services.svelte'
	import { ArrowUp } from 'carbon-icons-svelte';
	import { fly } from 'svelte/transition';

    let arrowUp = false

    function handleScrollTop () {
        if (window.scrollY <= 79) {
            arrowUp = false
        }
        else {
            arrowUp = true
        }
    }
</script>
<svelte:window on:scroll={handleScrollTop}/>
<div class="home-page-body">
    <Hero />
    <Services />
    <About />
    <WhyUs />
    <ContactUs />
    <Comments />
    <OurTeam />
    <Posts />
    <ContactUsForm />
    <Clients />
    <Footer/>
    <div class="scroll-top">
        {#if arrowUp}
        <button
        on:click={() => {window.scrollTo({
            top: 0, behavior: 'smooth'
        }
     
        )}} 
        in:fly="{{y: 50, duration: 1000}}" out:fly="{{y: 50, duration: 1000}}"
        class="arrow-up-short">
            <i><ArrowUp size={24} color="white"/></i>
        </button>
        {/if}
    </div>
</div>

<style lang="scss" global>
    @import '../app.scss';
    .scroll-top button {
        border: none;
        cursor: pointer;
        &:hover {
            background: rgba(248, 90, 64, 0.8);
        }
    }

.arrow-up-short {
    align-items: center;
    justify-content: center;    
    display: flex;
    position: fixed;
    opacity: 1;
    right: 15px;
    bottom: 15px;
    z-index: 99999;
    background: #000;
    width: 44px;
    height: 44px;
    border-radius: 50px;
    transition: all 0.4s;
}
</style>

