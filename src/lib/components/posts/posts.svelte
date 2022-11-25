<div id="posts">
    <header>
        <h2>Recent Blog Posts</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
    </header>
</div>

<style lang="scss">
    @use 'src/variables';

    #posts {
        color: variables.$paragraph-color;
        header {
            text-align: center;
            margin-bottom: 60px;
            h2 {
                font-weight: 600;
                color: variables.$h2-color;
            }
        }
    }
</style>