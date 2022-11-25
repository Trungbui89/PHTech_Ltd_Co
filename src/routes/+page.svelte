<script lang="ts">
    import About from '$lib/components/aboutUs/aboutUs.svelte'
    import Ourteam from '$lib/components/ourteam/ourteam.svelte'
    import WhyUs from '$lib/components/whyUs/whyUs.svelte'
	import Posts from '$lib/components/posts/posts.svelte'
</script>

<div class="home-page-body">
    <About />
    <WhyUs />
    <Ourteam />
    <Posts />
</div>

<style lang="scss" global>
    @import '../app.scss';
</style>
