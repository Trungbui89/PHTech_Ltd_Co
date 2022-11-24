<script lang="ts">
    import type { processData } from '$lib/store/homeStore/about'
    import { onMount } from 'svelte'
    export let processData: processData = {title: '', process: ''}
    let processor: HTMLElement

    onMount(() => {
        processor.style.width = processData.process
    })
</script>

<div class="process-bar">
    <div class="processor"/>
    <div class="current-processor" bind:this={processor}>{processData.title}</div>
</div>

<style lang="scss">
    @use 'src/variables';
    $bar: 16px;
    $padding-bar: 6px;

    .process-bar {
        position: relative;
        .processor {
            height: calc($bar + $padding-bar * 2);
            width: 100%;
            background-color: #dcdcdc2e;
            border-radius: calc(($bar + $padding-bar * 2) / 2);
            position: relative;
        }
        .current-processor {
            background-color: #30ba15;
            display: inline-block;
            padding: $padding-bar 10px $padding-bar;
            border-radius: calc(($bar + $padding-bar * 2) / 2);
            position: absolute;
            font-size: $bar;
            color: #fff;
            top: 0;
        }
    }
</style>