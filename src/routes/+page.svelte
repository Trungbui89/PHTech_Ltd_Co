<script lang="ts">
    import "carbon-components-svelte/css/all.css";
    import { Theme, Content } from "carbon-components-svelte";

    let theme = "white";
</script>

<Theme bind:theme />

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<Content>
    <slot />
</Content>
