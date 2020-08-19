<script>
    import {onMount} from "svelte";
    import Button from './Button.svelte';
    import Card from "./Card.svelte";
    import Overlay from "./Overlay.svelte";
    import Tooltip from "./Tooltip.svelte";
    import List from "./List.svelte";
    import Textfield from "./Textfield.svelte";

    export let gridElements;
    export let alignment = "center";
    export let justify = "center";
    export let textAlign = ""

    let dynamicSlot;
    let components = {"Button": Button, "Textfield": Textfield, "List": List, "Card": Card,
         "Overlay": Overlay, "Tooltip": Tooltip};

    $: if (dynamicSlot){
        console.log({...dynamicSlot});
    }
</script>

<style>

</style>
<div class="{`flex flex-wrap justify-${justify} items-${alignment} text-${textAlign}`}">
    {#each gridElements as gridElem}
        <div class="sm:w-1/2 md:w-1/3 lg:w-1/4 my-3 mx-2">
            {#if gridElem.type === "Card"}

                <Card {...gridElem.props}>
                   {#if gridElem.props.slotContent}
                        <svelte:component this={components[gridElem.props.slotContent.type]} 
                            {...gridElem.props.slotContent.props}/>
                    {/if}
                </Card>

            {:else if gridElem.type === "Button"}

                <Button
                    {...gridElem.props}
                    />

            {:else if gridElem.type === "Textfield"}

                <Textfield {...gridElem.props} />

            {:else if gridElem.type === "Overlay"}
                
                <Overlay {...gridElem.props}>

                    {#if gridElem.props.slotContent}
                        <svelte:component this={components[gridElem.props.slotContent.type]} 
                            {...gridElem.props.slotContent.props}/>
                    {/if}

                </Overlay>
            {:else if gridElem.type === "List"}

                <List {...gridElem.props} />

            {:else if gridElem.type === "Tooltip"}

                <Tooltip {...gridElem.props}>
                    <svelte:component this={components[gridElem.props.slotContent.type]} 
                            {...gridElem.props.slotContent.props}/>
                </Tooltip>

            {:else if gridElem.type === "Grid"}

                <svelte:self {...gridElem.props} />

            {:else}

                {@html gridElem.markup}
                
            {/if}
        </div>
    {/each}
</div>

