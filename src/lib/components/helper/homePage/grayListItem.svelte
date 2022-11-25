<script lang="ts">
    import { ArrowRight } from "carbon-icons-svelte"
    export let content: string = ''
</script>

<div class="gray-wrapper">
    <div class="gray-content">
        <div class="gray-icon">
            <ArrowRight />
        </div>
        <p>{content}</p>
    </div>
</div>

<style lang="scss">
    @use 'src/variables';

    .gray-wrapper {
        background-color: variables.$about-paragraph-color;
        padding: 15px 21px 15px 20px;
        border-radius: 8px;
        .gray-content {
            display: flex;
            flex-direction: row;
            align-items: center;
            .gray-icon {
                background-color: variables.$arrow-icon-bg;
                display: block;
                width: 16px;
                height: 16px;
                border-radius: 50%;
                margin-right: 6px;
                :global(svg) {
                    fill: white;
                }
            }
            p {
                font-size: 1.1rem;
            }
        }
    }
</style>