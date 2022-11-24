<script lang='ts'>
    export let value: string = ''
</script>

<div class="button-wrap">
    <p class="title">
        {value}
    </p>
</div>

<style lang="scss">
    @use 'src/variables';
    $btn: 18px;
    $padding-btn-tb: 16px;
    $padding-btn-rl: 45px;

    .button-wrap {
        background-color: variables.$h2-color;
        min-width: 150px;
        width: fit-content;
        border-radius: calc(($btn + $padding-btn-tb * 2) / 2);
        cursor: pointer;
        .title {
            display: block;
            font-size: $btn;
            color: #fff;
            padding: $padding-btn-tb $padding-btn-rl;
            text-align: center;
            line-height: 1;
            transition: all ease-in-out .3s;
        }
        &:hover .title {
            color: variables.$arrow-icon-bg;
        }
    }
</style>