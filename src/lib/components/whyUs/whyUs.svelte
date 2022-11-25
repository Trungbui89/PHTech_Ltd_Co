<script lang="ts">
    import { Grid, Row, Column } from "carbon-components-svelte"
    import GrayListItem from "../helper/homePage/grayListItem.svelte"
    import LevelProcessBar from "../helper/homePage/levelProcessBar.svelte"
    import Button from "../helper/homePage/button.svelte"

    let grayList = [
        "Nemo enim ipsam voluptatem quia voluptas sit aspernatur",
        "Sed quia consequuntur magni dolores eos qui ratione",
        "Neque porro quisquam est, qui dolorem ipsum quia amet",
        "Consectetur, adipisci velit, sed quia non numquameius",
        "Rempora incidunt ut labore et dolore magnam aliquam",
        "Neque porro quisquam est, qui dolorem ipsum quia amet"
    ]
</script>

<section id="whyUs">
    <div class="whyUs-wrapper">
        <header>
            <h2>Why Us</h2>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
        </header>
        <div class="whyUs-content">
            <Grid>
                <Row>
                    <Column sm={1} md={8} lg={8}>
                        <div class='why-us-img'>
                            <img src='/images/whyus.jpg' />
                        </div>
                    </Column>
                    <Column sm={1} md={8} lg={8}>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Xonsectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                        <ul class="gray-list">
                            {#each grayList as item}
                                <li>
                                    <GrayListItem content={item} />
                                </li>
                            {/each}
                        </ul>
                    </Column>
                </Row>
            </Grid>
        </div>
    </div>
</section>

<style lang="scss">
    @use 'src/variables';

    #whyUs {
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
        .whyUs-content {
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