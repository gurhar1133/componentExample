<script>
    import {createEventDispatcher} from "svelte";
    import Listbutton from "./Listbutton.svelte";
    export let title = "";
    export let singeLine = true;
    export let twoLine = false;
    export let threeLine = false;
    export let items;
    export let rounded = false;
    export let shaped  = false;

    const dispatch = createEventDispatcher();
    
    let list_template = `my-4 border border-gray-400 shadow-md rounded w-full max-w-sm h-full`;
    
    // let listItems1 = [{name: "item1"}, {name: "item2" }, {name:"item3" }, {name: "item4"}];

    // let listItems2 = [
    //                 {name: "item1", secondary:"THis is a test"},
    //                 {name: "item2", secondary:"THis is also a test" }, 
    //                 {name:"item3", secondary:"THis is another test" }, 
    //                 {name: "item4", secondary:"Yet another test"}
    //                 ];

    
    
</script>

<style>
.list{
    height: max-content;
}
</style>

<div class="{list_template}">
    <h4 class="text-base text-gray-600 py-3 px-3 list">{title.toUpperCase()}</h4>
    
    {#each items as item (Math.random().toString())}
        <Listbutton
            object="{item}"
            singeLine="{singeLine}"
            twoLine="{twoLine}"
            threeLine="{threeLine}"
            rounded="{rounded}"
            shaped="{shaped}"
        />
    {/each}
   
</div>

<!-- Lists:
	Title: string
	SingleLine: boolean (true by default)
	TwoLine: boolean (false by default)
	ThreeLine: boolean (false by default)
	Rounded: boolean  (false by default)
	Shaped: boolean   (false by default)
	Items: either a list with objects {name: “name1”}...
		Two line: {name: “name1”, secondary: “secondary1”}...
		Three line: {name: “name1”, secondary: “secondary1”, ternary: “ternary1”}.... -->