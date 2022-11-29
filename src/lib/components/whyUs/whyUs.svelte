<script lang="ts">
    import { Grid, Row, Column } from "carbon-components-svelte"
    import GrayListItem from "../helper/homePage/grayListItem.svelte"
    import LevelProcessBar from "../helper/homePage/levelProcessBar.svelte"
    import Button from "../helper/homePage/button.svelte"
    import { inview } from 'svelte-inview';
	import { fade, fly } from "svelte/transition";

    let grayList = [
        "Nemo enim ipsam voluptatem quia voluptas sit aspernatur",
        "Sed quia consequuntur magni dolores eos qui ratione",
        "Neque porro quisquam est, qui dolorem ipsum quia amet",
        "Consectetur, adipisci velit, sed quia non numquameius",
        "Rempora incidunt ut labore et dolore magnam aliquam",
        "Neque porro quisquam est, qui dolorem ipsum quia amet"
    ]
    let isInView: boolean;
    let isInView1: boolean;

</script>

<section id="why-us">
    <div class="why-us-wrapper"
    use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
    on:change={({ detail }) => {
        isInView = detail.inView;
    }}>
        {#if isInView}
        <div class="why-us-title"
        in:fade="{{duration: 1500}}">
            <header>
                <h2>Why Us</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
            </header>
        </div>
        {/if}                
        <div class="why-us-content"
        use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
        on:change={({ detail }) => {
        isInView1 = detail.inView;
        }}>
        {#if isInView1}
            <Grid>
                <Row>
                    <Column sm={1} md={8} lg={8}>
                        <div class='why-us-img'
                        in:fly="{{x: -100, opacity: 0, duration: 1500, delay:500}}">
                            <img src='/images/whyus.jpg' />
                        </div>
                    </Column>
                    <Column sm={1} md={8} lg={8}>
                        <div class="why-us-right-list"
                        in:fly="{{x: 100, opacity: 0, duration: 1500, delay:500}}">
                            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Xonsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                            <ul class="gray-list">
                                {#each grayList as item}
                                    <li>
                                        <GrayListItem content={item} />
                                    </li>
                                {/each}
                            </ul>
                        </div>
                    </Column>
                </Row>
            </Grid>
        {/if}
        </div>
    </div>
</section>

<style lang="scss">
    @use 'src/variables';

    #why-us {
        padding: 90px 0;
        overflow: hidden;
        width: variables.$wrapper-width-des;
        margin: 0 auto;
        font-weight: 600;
        color: variables.$paragraph-color;
        font-family: 'Poppins', sans-serif;
        header {
            text-align: center;
            padding-bottom: 60px;
            h2 {
                color: variables.$h2-color;
                font-size: 32px;
                font-weight: 600;
                font-family: 'Poppins', sans-serif;
                text-shadow: 0 0 1px #000;
            }
            p {
                margin-top: 12px;
            }
        }
        .why-us-content {
            padding: 0 48px;
            p {
                margin-bottom: 12px;
            }
            .gray-list {
                li {
                    padding: 6px 0;
                }
            }
            .why-us-img {
                display: flex;
                max-width: 100%;
                height: 100%;
                align-items: center;
                img {
                    max-width: 100%;
                }
            }
        }
    }
</style>