<script lang="ts">
	import { Column, Grid, Row } from "carbon-components-svelte";
	import { ApplicationWeb, IbmMq, VirtualDesktop } from "carbon-icons-svelte";
    import { inview } from 'svelte-inview';
	import { fade, fly } from "svelte/transition";

    let services = [
        {icon: ApplicationWeb, category: 'Application Design', text: 'Ronsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'},
        {icon: IbmMq, category: 'Application Design', text: 'Ronsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'},
        {icon: VirtualDesktop, category: 'Application Design', text: 'Ronsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'}
    ]
    let isInView: boolean;
</script>

<section id="services"
use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
on:change={({ detail }) => {
    isInView = detail.inView;
}}>
    <div class="services-container">
       {#if isInView}
        <div class="services-content-wrap">
            <Grid>
                <Row style="justify-content: space-between">
                    {#each services as service, i}
                    <Column 
                    lg={5}>
                        <div class="icon-box"
                        in:fly="{{y: 200, opacity: 0, duration: 1500, delay:100*i}}">
                            <div class="icon">
                                <i><svelte:component this={service.icon} size={50}/></i>
                            </div>
                            <h4 class="title">
                                <a href="" class="stretched-link">
                                    {service.category}
                                </a>
                            </h4>
                            <p>{service.text}</p>
                        </div>
                    </Column>
                    {/each}
                </Row>
            </Grid>
        </div>
        {/if}
    </div>
</section>

<style lang="scss">
@use 'src/variables';
#services {
    padding: 90px 0;
    overflow: hidden;
    height: 100%;
}
.services-container {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
}
.services-content-wrap {
    width: 93%;
}
.icon-box {
    padding: 50px 30px;
    position: relative;
    overflow: hidden;
    background: #ffffff;
    box-shadow: 0 0 2px 0 rgb(255 39 7 / 28%);
    border-radius: 0;
    z-index: 1;
    height: 100%;
    width: 100%;
    text-align: center;
    transition: all 0.3s ease-in-out;
    .icon {
        margin-bottom: 20px;
        padding-top: 10px;
        display: inline-block;
        transition: all 0.3s ease-in-out;
        font-size: 48px;
        line-height: 1;
        color: rgb(0 0 0 / 60%);
    }
    .title {
        font-weight: 700;
        margin-bottom: 15px;
        font-size: 24px;
        transition: all 0.3s ease-in-out;
        a {
            transition: all 0.3s ease-in-out;
            color: #30ba15;
            text-decoration: none;
        }
    }
    p {
        transition: all 0.3s ease-in-out;
        margin-top: 0;
    }
}
.icon-box:hover {
    background: #222222;
    .icon {
        color: #fff;
    }
    .title {
        color: #fff;
        a {
        color: #fff;
        }
    }
    p {
        color: #fff;
    }
}
</style>    