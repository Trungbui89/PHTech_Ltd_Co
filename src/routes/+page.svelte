<script lang="ts">

    import OurTeam from '$lib/components/ourteam/ourteam.svelte';
    import ContactUsForm from '$lib/components/contactUsForm/contactUsForm.svelte';
    import About from '$lib/components/aboutUs/aboutUs.svelte'
    import Ourteam from '$lib/components/ourteam/ourteam.svelte'
    import WhyUs from '$lib/components/whyUs/whyUs.svelte'
</script>

<div class="home-page-body">
    <div class="open">
        <input type="checkbox" bind:checked={open}> Open Our Team
    </div>
    <OurTeam 
    ourteamAnimation={true}
    ourteamAnimation2={true}
    ourteamAnimation3={true}
    ></OurTeam>
    <div class="open">
        <input type="checkbox" bind:checked={open1}> Open Contact Us Form
    </div>
    <ContactUsForm
    contactUsFormAnimation={true}>
    </ContactUsForm>
    <div class="open">
        <input type="checkbox" bind:checked={open1}> Open About Us
    </div>  
    <About />
    <div class="open">
        <input type="checkbox" bind:checked={open1}> Open Why Us
    </div>  
    <WhyUs />
</div>

<style lang="scss">
.open {
    display: flex;
    align-content: center;
    justify-content: center;
}
</style>

