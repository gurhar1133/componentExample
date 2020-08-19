<script>
    import Icon from 'svelte-awesome';
    import {createEventDispatcher} from "svelte";
    export let items;
    export let icons;
    export let color = 'bg-red-600';
    
    const dispatch = createEventDispatcher();

    let hoverColor = 'bg-red-700';
    if (color === "primary"){
        color = 'bg-blue-600';
        hoverColor = "bg-blue-700";
    }

</script>

<style>
.z-footer{
    z-index: 100;
}
</style>
<div class="{`fixed mx-0 z-footer left-0 bottom-0 w-full ${color} text-gray-800`}">
    <div class="flex justify-center ">
        {#each items as item (item.id)}
            <div on:click={()=>{
                dispatch("click", item.id);
            }} class="{`rounded-full hover:${hoverColor} cursor-pointer my-3 mx-2 py-3 px-4 px-2`}">{item.name}</div>
        {/each}
        {#each icons as icon (icon.id)}
            <div on:click={()=>{
                    dispatch("click", icon.id);
            }} class="{`rounded-full hover:${hoverColor} cursor-pointer my-3 mx-2 py-3 px-4 px-2`}">
                <Icon data={icon.name}/>
            </div>
        {/each}
    </div>
    <hr class='border-gray-800 shadow-xl'>
    <h4 class="my-4 text-white text-center text-sm">Svelte Footer 2020</h4>
</div>