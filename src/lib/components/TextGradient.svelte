<script lang="ts">

    /** hex color */
    export let from: string;
    /** hex color */
    export let via: string|undefined = undefined;
    /** hex color */
    export let to: string;

    export let className;
</script>

<span class={className} style={`background-image: linear-gradient(to right, ${from},${via ? ' '+via+',' : ''} ${to}); color: transparent; background-clip: text;`}>
    <slot></slot>
</span>