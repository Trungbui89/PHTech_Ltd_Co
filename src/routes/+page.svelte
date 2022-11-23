<script lang="ts">
    import "carbon-components-svelte/css/all.css";
    import { Theme, Content } from "carbon-components-svelte";

    let theme = "white";
</script>

<Theme bind:theme />

<div class="top-bar">

</div>
<Content>
    <slot />
</Content>

<style lang="scss">
    
</style>