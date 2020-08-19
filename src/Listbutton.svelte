<script>
    import {createEventDispatcher} from "svelte";
    export let object;
    export let singeLine = true;
    export let twoLine = false;
    export let threeLine = false;
    export let rounded = false;
    export let shaped  = false;
    const dispatch = createEventDispatcher();
    let mouseX;
    let mouseY;
    let circleClass;

    let item_shape = shaped ? "rounded-tr-full rounded-br-full" : "";
    let item_rounded = rounded ? "rounded-full" : "";
    let item_template = `overflow-hidden relative py-3 px-5 hover:bg-gray-200 block w-full border-0 text-left 
                            focus:text-blue-800 focus:outline-none ${item_rounded}
                            ${item_shape}`;
    let temp = item_template;

    function onClick(event){
       
        circleClass = "circle";
       
        mouseX = event.offsetX - 15;
        mouseY = event.offsetY - 15;

        setTimeout(()=>{
            circleClass = "";
        },300);

    }
    function onFocus(){
        
        setTimeout(()=>{
            item_template += " focus:bg-blue-200 focus:bg-opacity-50";
        },300);
    }
    function onBlur(){
        item_template = temp;
    }

</script>

<style>

.circle{
        animation: ripple 0.3s linear;
        position: absolute;
        border-radius: 50%;
        height: 50px;
        width: 50px;
        transform: scale(0);
        z-index: 99;
        background-color: rgba(0, 153, 255, 0.4);
        
    }
@keyframes ripple{
        to{
            transform: scale(10);
            opacity: .3;
        }
    }
</style>

<button on:click on:click={onClick} on:focus={onFocus} on:blur={onBlur} class="{item_template}">
            <h4 class="">{object.name}</h4>
            {#if twoLine || threeLine}
                <h4 class="text-sm">{object.secondary}</h4>
            {/if}
            {#if threeLine}
                <h4 class="text-sm">{object.ternary}</h4>
            {/if}
        <div class="{circleClass}" style="{`top:${mouseY}px; left:${mouseX}px;`}"> </div>
</button>