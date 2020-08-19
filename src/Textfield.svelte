<script>
    export let filled = false;
    export let outlined = false;
    export let placeHolder;
    let fill = filled ? "bg-gray-200" : "";
    let outline = outlined ? "" : "border-0 focus:outline-none";
    let textfield_template = `mx-3 ${outline} ${fill} py-2 px-2 w-full rounded`;
    let focusEffect;
    
    function onFocus(){
        focusEffect =  "focus-effect-bottom";
    }
    function onBlur(){
        focusEffect = "";
    }
</script>

<style>
.focus-effect-bottom{
    animation: fillout 0.27s linear;
    border-bottom-color: rgba(3, 129, 212, 0.9);
    border-bottom-width: 2px;
    
    
    
}

@keyframes fillout{
    from {
        transform: scaleX(0);
    }
    to{
        transform: scaleX(1);
    }
}

</style>

<div class="inline-block mx-1" >
    {#if !outlined}
        <input placeholder="{placeHolder}" on:focus={onFocus} on:blur={onBlur} class="{textfield_template}" type="text">
    
            <hr class="{`mx-3 w-full ${focusEffect}`}">
        
    {:else if outlined}
        <input placeholder="{placeHolder}" on:focus={onFocus} on:blur={onBlur} class="{textfield_template}" type="text"> 
    {/if}
</div>
