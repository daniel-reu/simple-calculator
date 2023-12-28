<script lang="ts">

    export let variation: Variation;
    export let onClick: Function;
    export let value: string = "";

    type Variation = "default" | "action";

    const variations: Record<string, string> = {
    'default': 'bg-slate-500 hover:bg-slate-400 active:bg-slate-300 h-[60px] w-[60px] select-none',
    'action': 'bg-orange-500 hover:bg-orange-400 active:bg-orange-300 h-[60px] w-[60px] select-none',
    };

    const classList: string = variations[variation] || "";
</script>

<button on:click="{onClick(value)}" class="{classList}">
    {#if value}
        {value}
    {:else if !value}
        <slot></slot>
    {/if}
</button>