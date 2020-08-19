<script>
    import {scale} from "svelte/transition";
    export let position;
    export let openOnClick = false;
    export let openOnHover = true;

    let posClass;
    let display = false;
    let toolText = "Tooltip";

    if (position === "top"){
        posClass = "absolute tool-top";
    }
    else if (position === "bottom"){
        posClass = "absolute tool-bottom";
    }
    else if (position === "left"){
        posClass = "absolute tool-left";
    }
    else if (position === "right"){
        posClass = "absolute tool-right";
    }

</script>
<style>
    .tooltip{
        width: min-content;
    }
    .tool-bottom{
        left: 25%;
    }
    .tool-top{
        top: -120%;
        left: 25%;
    }
    .tool-left{
        top: -5%;
        left: -22%;
    }
    .tool-right{
        top: -5%;
        right: -22%;
    }
    .wrapper{
        z-index: 0;
    }
</style>



<div class="relative wrapper">

    {#if openOnHover}
        <div on:mouseenter={()=>{display = !display}} 
            on:mouseleave={()=>{display = !display}}
            class="cursor-pointer">
            <slot >

            </slot>
        </div>

        <div class="{posClass}">
            {#if display}
                <div transition:scale={{duration: 300}} class="rounded tooltip px-4 py-1 bg-gray-600 text-white bg-opacity-75 text-center">{toolText}</div>
            {/if}
        </div>
    {:else if openOnClick}
        <div on:click={()=>{display = !display}} class="cursor-pointer">
            <slot >

            </slot>
        </div>

        <div class="{posClass}">
            {#if display}
                <div transition:scale={{duration: 300}} class="rounded tooltip px-4 py-1 bg-gray-600 text-white bg-opacity-75 text-center">{toolText}</div>
            {/if}
        </div>
    {/if}

</div>




