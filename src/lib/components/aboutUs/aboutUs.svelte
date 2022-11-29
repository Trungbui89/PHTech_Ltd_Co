<script lang="ts">
    import { Grid, Row, Column } from "carbon-components-svelte"
    import GrayListItem from "../helper/homePage/grayListItem.svelte"
    import LevelProcessBar from "../helper/homePage/levelProcessBar.svelte"
    import Button from "../helper/homePage/button.svelte"
    import { inview } from 'svelte-inview'
	import { fly, fade } from "svelte/transition";
	import ContactUs from "../contactUs/contactUs.svelte";

    let grayList = [
        "Nemo enim ipsam voluptatem quia voluptas sit aspernatur",
        "Sed quia consequuntur magni dolores eos qui ratione",
        "Neque porro quisquam est, qui dolorem ipsum quia amet",
        "Consectetur, adipisci velit, sed quia non numquameius",
        "Rempora incidunt ut labore et dolore magnam aliquam",
        "Neque porro quisquam est, qui dolorem ipsum quia amet"
    ]

    let processList = [
        {title: "TDD", process: "15%"},
        {title: "Python", process: "30%"},
        {title: "C#", process: "45%"},
        {title: "CSS3", process: "60%"},
        {title: "JavaScript", process: "75%"},
        {title: "HTML5", process: "90%"},
        {title: "React", process: "65%"}
    ]

    let isInView: boolean;
    let isInView1: boolean;

</script>

<section id="about">
    <div class="about-wrapper">
        <div class="about-header"
            use:inview={{ unobserveOnEnter: true, rootMargin: '-20%'}}
            on:change={({ detail }) => {
                isInView = detail.inView;
            }}>
            {#if isInView}
            <header
            in:fly="{{y: 200, opacity: 0, duration: 1500, delay:100}}">
                <h2>About Us</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
            </header>
            {/if}
        </div>
        <div class="about-content"
        use:inview={{ unobserveOnEnter: true, rootMargin: '-20%',threshold:1 }}
            on:change={({ detail }) => {
                isInView1 = detail.inView;
            }}>
            {#if isInView1}
            <Grid>
                <Row>
                    <Column sm={1} md={8} lg={8}>
                        <div class="left-list"
                        in:fly="{{x: 100, opacity: 0, duration: 1500, delay:500}}">                            
                            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Xonsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                            <ul class="gray-list">
                                {#each grayList as item}
                                    <li>
                                        <GrayListItem content={item} />
                                    </li>
                                {/each}
                            </ul>
                            <div class="btn-position">
                                <Button value="Get Started"/>
                            </div>
                        </div>
                    </Column>
                    <Column sm={1} md={8} lg={8}>
                        <div class="right-list"
                        in:fly="{{x: -100, opacity: 0, duration: 1500, delay:500}}">
                            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Xonsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                            <ul class="process-list">
                                {#each processList as item}
                                    <li>
                                        <LevelProcessBar processData={item} />
                                    </li>
                                {/each}
                            </ul>
                            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore</p>
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

    #about {
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
        .about-content {
            padding: 0 48px;
            p {
                margin-bottom: 12px;
            }
            .gray-list {
                li {
                    padding: 6px 0;
                }
            }
            .process-list {
                padding: 6px 0;
                li {
                    margin-bottom: 20px;
                    
                }
            }
            .btn-position {
                margin-top: 20px;
            }
        }
    }
</style>