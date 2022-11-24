<script lang="ts">
import "carbon-components-svelte/css/all.css"
import { Grid, Row, Column } from "carbon-components-svelte";
import { fade, fly } from "svelte/transition";

export let checkAnimation = false
export let checkAnimation2 = false
export let checkAnimation3 = false

</script>
<section id="team">
    <div class="our-team-content">
        {#if checkAnimation}
        <div class="our-team__header">
            <h2>Our Team</h2>    
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
        </div>
        {/if}
        {#if checkAnimation2}
        <div class="our-team__member">
            <Grid>
                <div class="our-team__ceo"
                in:fly="{{ x: -1000, duration: 1500 }}" out:fly="{{ x: -1000, duration: 1500 }}">
                <Row>
                    <Column sm={1} md={4} lg={4}>
                            <div class="member">
                                <div class="avatar">
                                    <img src="/images/avatar1.jpeg">
                                </div>
                                <h4>Quyền Lê</h4>
                                <span>Manager</span>
                            </div>
                    </Column>
                    <Column sm={1} md={4} lg={4}>
                        <div class="member">
                            <div class="avatar">
                                <img src="/images/avatar1.jpeg">
                            </div>
                            <h4>Huy Đinh</h4>
                            <span>Manager</span>
                        </div>
                    </Column>
                </Row>
                <div class="underline ceo">
                    <span in:fade out:fade>CEO</span>
                </div>   
                <hr in:fly="{{ x: -1000, duration: 1500 }}" out:fly="{{ x: -1000, duration: 1500 }}">   
                </div>
                {#if checkAnimation3}
                <div class="our-team__dev"
                in:fly="{{ x: 1000, duration: 1500 }}" out:fly="{{ x: 1000, duration: 1500 }}">  
                <Row>
                    <Column sm={{ span: 4, offset: 1 }}>
                        <Grid>
                            <Row>
                                <Column sm={1} md={4} lg={4}>
                                        <div class="member">
                                            <div class="avatar">
                                                <img src="/images/avatar1.jpeg">
                                            </div>
                                            <h4>Trung Bùi</h4>
                                            <span>Website Developer</span>
                                        </div>
                                </Column>
                                <Column sm={1} md={4} lg={4}>
                                    <div class="member">
                                        <div class="avatar">
                                            <img src="/images/avatar1.jpeg">
                                        </div>
                                        <h4>Đinh Việt</h4>
                                        <span>Website Developer</span>
                                    </div>
                                </Column>
                                <Column sm={1} md={4} lg={4}>
                                    <div class="member">
                                        <div class="avatar">
                                            <img src="/images/avatar1.jpeg">
                                        </div>
                                        <h4>Trần Phan</h4>
                                        <span>Website Developer</span>
                                    </div>
                                </Column>
                            </Row>              
                        </Grid>
                    </Column>
                </Row>
                <div class="underline dev">
                    <span in:fade out:fade>Developer Team</span>  
                </div> 
            </div>
            <hr in:fly="{{ x: 1000, duration: 1500 }}" out:fly="{{ x: 1000, duration: 1500 }}">
            {/if}   
            </Grid>
        </div>
        {/if}
    </div>
</section>

<style lang="scss">
@use 'src/variables';

.our-team-content {
    background: linear-gradient(rgb(7 7 7 / 60%), rgb(0 0 0 / 60%)), url(/images/background2.jpeg) center center;
    background-size: cover;
    padding: 150px 60px;
    border-radius: 0px;
    overflow: hidden;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center;
}
.our-team__header {
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
.underline {
    display: flex;
    position: relative;
    &.ceo {
        justify-content: flex-end;
    }
    &.dev {
        justify-content: flex-start;
    }
    span {
        font-size: 32px;
        font-weight: 600;
        margin-bottom: 20px;
        position: absolute;
        color: #fff;
        font-style: italic;
        top: -35px;
    }
}
.member {
    text-align: center;
    border-radius: 10px;
    padding: 15px;
    overflow: hidden;
    img {
        border-radius: 0;
        overflow: hidden;
        width: 100%;
        height: 100%;
    }
    h4 {
        font-weight: 700;
        margin-top: 16px;
        margin-bottom: 2px;
        font-size: 20px;    
        color:#fff;
    }
    span {
        color:#fff;
        font-style: italic;
        display: block;
        font-size: 14px;
    }
}
</style>