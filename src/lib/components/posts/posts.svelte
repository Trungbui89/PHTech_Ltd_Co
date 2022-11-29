<script lang="ts">
    import { Grid, Row, Column } from "carbon-components-svelte";
    import { fade, fly } from "svelte/transition";
    import { inview } from 'svelte-inview';

    let posts = [
        {category:"Domain & Hosting", title: "How to host website on any hosting provider?", author: "William Bla", date: "Feb 1, 2022", src: "/images/blog-1.jpeg"},
        {category:"Advertisement", title: "How to create add on google adwords?", author: "Jobi Ret", date: "Oct 5, 2022", src: "/images/blog-2.jpeg"},
        {category:"Marketing", title: "What is digital marketing and why is important?", author: "Main Dow", date: "Dec 22, 2022", src: "/images/blog-3.jpeg"}
    ]
    let isInView: boolean;

</script>
<section id="posts"
use:inview={{ unobserveOnEnter: true, rootMargin: '-20%' }}
on:change={({ detail }) => {
    isInView = detail.inView;
}}>
    {#if isInView}
    <div class="posts-content">
        <header class="posts-header"
        in:fly="{{ y: 100, duration: 1500 }}">
            <h2>Recent Blog Posts</h2>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
        </header>
        <div class="posts-content-wrap">
            <Grid>
                <Row style="justify-content: space-between">
                    {#each posts as article}
                    <Column 
                    lg={5}
                    padding>
                    <article class="post-item"
                    in:fly="{{ y: 100, duration: 1500 }}">
                        <div class="post-img">
                            <img src={article.src} alt="">
                        </div>
                        <div class="post-info-box">
                            <p class="post-category">{article.category}</p>
                            <h2 class="post-title">{article.title}</h2>
                            <div class="post-meta">
                                <p class="post-author">{article.author}</p>
                                <p class="post-date">
                                    {article.date}
                                </p>
                            </div>
                        </div>
                    </article>
                    </Column>
                    {/each}
                </Row>
            </Grid>
        </div>
    </div>
    {/if}
</section>

<style lang="scss">
@use 'src/variables';
#posts {
    background: linear-gradient(rgb(7 7 7 / 60%), rgb(0 0 0 / 60%)), url(/images/background2.jpeg) center center;
    background-size: cover;
    padding: 0 60px 150px;
    border-radius: 0px;
    overflow: hidden;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center;
}
.posts-content {
    width: variables.$wrapper-width-des;
    margin: 0 auto;
}
.posts-header {
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
.posts-content-wrap {
    display: flex;
    flex-wrap: wrap;
}
.post-item {
    box-shadow: 0 1px 6px rgb(0 0 0 / 10%);
    background-color: #464946;
    padding: 30px 30px 71px 30px;
    height: 100%;
    overflow: hidden;
    text-align: left;
    justify-content: center;
    align-items: flex-start;
}
.post-img {
    max-height: 240px;
    margin: -30px -30px 15px -30px;
    overflow: hidden;
    img {
        max-width: 100%;
        height: auto;
        vertical-align: middle;
    }
}
.post-category {
    font-size: 16px;
    margin-bottom: 10px;
    color: #fff;
}
.post-title {
    font-size: 22px;
    font-weight: 700;
    padding: 0;
    margin: 0 0 20px 0;
    color: #fff;
}
.post-author {
    font-weight: 600;
    margin-bottom: 5px;
    color: #fff;
}
.post-date {
    font-size: 14px;
    color: #fff;
    margin-bottom: 0;
}
</style>