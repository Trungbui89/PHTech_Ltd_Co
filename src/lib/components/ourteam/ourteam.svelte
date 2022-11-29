<script lang="ts">
import "carbon-components-svelte/css/all.css"
import { Grid, Row, Column } from "carbon-components-svelte";
import { fade, fly, draw, crossfade, scale, slide } from "svelte/transition";
import { inview } from 'svelte-inview';

let isInView: boolean;
let phuhuyenCeos = [
    {img:'/images/avatar1.jpeg', name: 'Quyền Lê', office: 'Manager'},
    {img:'/images/avatar1.jpeg', name: 'Huy Đinh', office: 'Manager'},
]
let phuhuyenStaffs = [
    {img:'/images/avatar2.jpg', name: 'Trung Bùi', office: 'Website Developer'},
    {img:'/images/avatar3.jpg', name: 'Đinh Việt', office: 'Website Developer'},
    {img:'/images/avatar4.jpg', name: 'Trần Phan', office: 'Website Developer'},
    
]   
</script>
<section id="team">
    <div class="our-team-content"
    use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
    on:change={({ detail }) => {
        isInView = detail.inView;
    }}>
        {#if isInView}
        <header class="our-team__header"
        in:fade="{{duration: 1500}}">
            <h2>Our Team</h2>    
            <p>Our business is helping you grow your business</p>
        </header>
        {/if}
        {#if isInView}
        <div class="our-team__member">
            <Grid>
                <div class="our-team__ceo"
                >
                    <Row>
                        {#each phuhuyenCeos as ceo, i}
                        <Column sm={1} md={4} lg={4}>
                                <div class="member"
                                in:scale="{{duration: 1500, start: 1.5, opacity: 0, delay: 500*i}}">
                                    <div class="avatar">
                                        <img src={ceo.img}>
                                    </div>
                                    <h4>{ceo.name}</h4>
                                    <span>{ceo.office}</span>
                                </div>
                            </Column>
                        {/each}
                    </Row>
                <div class="underline ceo">
                    <span in:fade out:fade>CEO</span>
                </div>   
                <hr in:fly="{{ x: -1000, duration: 1500 }}">   
                </div>
                {#if isInView}
                <div class="our-team__dev">  
                    <Row style="justify-content: flex-end">
                        {#each phuhuyenStaffs as staff, i}
                            <Column sm={1} md={4} lg={4}>
                                    <div class="member"
                                    in:scale="{{duration: 1500, start: 1.5, opacity: 0, delay: 500*(phuhuyenStaffs.length - i -1)}}">
                                        <div class="avatar">
                                            <img src={staff.img}>
                                        </div>
                                        <h4>{staff.name}</h4>
                                        <span>{staff.office}</span>
                                    </div>
                            </Column>
                        {/each}
                    </Row>
                    <div class="underline dev">
                        <span in:fade out:fade>Developer Team</span>  
                    </div> 
                </div>
                <hr in:fly="{{ x: 1000, duration: 1500 }}">
                {/if}   
            </Grid>
        </div>
        {/if}
    </div>
</section>

<style lang="scss">
@use 'src/variables';
#team {
    background: linear-gradient(rgb(7 7 7 / 60%), rgb(0 0 0 / 60%)), url(/images/background2.jpeg) center center;
    background-size: cover;
    padding: 150px 60px;
    border-radius: 0px;
    overflow: hidden;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center;
}
.our-team-content {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
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
        font-family: 'Poppins', sans-serif;
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
        font-family: 'Poppins', sans-serif;
    }
    span {
        color:#fff;
        font-style: italic;
        display: block;
        font-size: 14px;
        font-family: 'Poppins', sans-serif;
    }
}
</style>