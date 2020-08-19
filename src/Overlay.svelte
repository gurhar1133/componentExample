<script>
    import Card from "./Card.svelte";
    import {fly} from "svelte/transition";
    export let absolute = false; 
    export let opacity = .45;
    export let zIndex = "10";
    export let value = false;

    let bgOpacity;

    if (opacity >= 0 && opacity < .25){
        bgOpacity = "bg-opacity-25";
    }
    else if (opacity >= .25 && opacity < .50){
         bgOpacity = "bg-opacity-50";
    }
    else if (opacity >= .50 && opacity < 1){
        bgOpacity = "bg-opacity-75";
    }
    else if (opacity >= 1){
        bgOpacity = "bg-opacity-100";
    }
    else{
        console.log('overlay ERROR');
    }
    
    let abs_position = absolute ? "absolute modal-backdrop-abs top-0 left-0 h-full w-full" : "modal-backdrop-full relative";
    let overlay_template = `${abs_position} ${bgOpacity} bg-gray-800`;
    let slot_template = `top-auto left-auto z-50`;

    $: hidden = value ? " block" : " hidden"

</script>
<style>
    .abs{
        top: 0px;
    }
    .modal-backdrop-abs{
        
    }
    .modal-backdrop-full{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        
        z-index: 100;
    }
    .slot-content{
       opacity: 10;
        position: absolute; 
        top: 20%;
        left: 35%;
        z-index: 100;
        
        
    }
</style> 

<div on:click={()=>{
        value = !value;
    }}
    class="{overlay_template + hidden}">

{#if value}
    <div on:click={()=>{
        value = false;
    }} transition:fly="{{duration: 500, y:800}}" class="{`${hidden} slot-content`}"> 
        <slot>
        </slot>
        
    </div>
{/if} 

</div>