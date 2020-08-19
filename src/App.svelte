<script>
  import Tailwindcss from "./Tailwindcss.svelte";

  // Icon imports will be needed in your components
  import Icon from 'svelte-awesome';
  import { faThumbsUp, faThumbsDown } from '@fortawesome/free-regular-svg-icons';
  import { beer, refresh, comment, codeFork, camera, ban } from 'svelte-awesome/icons';

  import Button from './Button.svelte';
  import Card from "./Card.svelte";
  import Overlay from "./Overlay.svelte";
  import Footer from "./Footer.svelte";
  import Tooltip from "./Tooltip.svelte";
  import List from "./List.svelte";
  import Textfield from "./Textfield.svelte";
  import Grid from "./Grid.svelte";
  


  let navItems = [{name: "Home", id: "1"}, {name : "Contact", id : "2"}];
  let navIcons = [{name : beer, id: "3"}, {name : comment, id : "4"}];

  let overlay1 = false;
  let overlay2 = false;
  $: overlay3 = false;
  $: console.log(overlay3);
  let listItems1 = [{name: "item1"}, {name: "item2" }, {name:"item3" }, {name: "item4"}];

  let listItems2 = [
                    {name: "item1", secondary:"THis is a test"},
                    {name: "item2", secondary:"THis is also a test" }, 
                    {name:"item3", secondary:"THis is another test" }, 
                    {name: "item4", secondary:"Yet another test"}
                    ];
  // See Grid components instructions below for how to deal with this.
  $: gridItems = [
      {
        type: "Card", props: {
          title: "Card Test", 
          subtitle: "Test", 
          description: "Lorem ipsum blah blah blah",
          hasImage: true,
          imgSrc: "https://www.pngkey.com/png/detail/767-7671067_minecraft-pixel-art-grid.png",
          shaped: true
        }
        
      },
      {
        type: "Card", props:{
          title: "Card Test2", 
          subtitle: "Test", 
          description: "Lorem ipsum blah blah blah",
          hasImage: true,
          imgSrc: "https://www.lysergic.net/wp-content/uploads/2017/07/figure_grid_dimple_dylan_bakker-750x1000.jpg",
          shaped: true,
          slotContent: {
            type: "Button",
            props: {
              btnText: "Slot",
              outlined: true,
              color: "secondary"
              }
            }
          }
        
      },
      {
        type: "Card", 
        props: {
          title: "Card Test3", 
          subtitle: "Test", 
          description: "Lorem ipsum blah blah blah",
          hasImage: true,
          imgSrc: "https://images.artistrunwebsite.com/arwblog/bg_37311453262250.jpg?1453262251",
          shaped: true
        }
        
      },
      {
        markup: "<h3 class='text-xl' style='color:red;'>Hello World</h3>"
      },
      {
        type: "Button",
        props: {
          btnText: "Click me!",
          elevation: "lg",
          rounded: true,
          textMode: true
        }
        
      },
      {
        type: "Textfield",
        props: {
          outlined: true
        }
        
      },
      {
        type: "Textfield",
        props: {
          filled: true
        }
        
      },
      {
        type: "Textfield",
        props: {
          placeHolder: "test"
        }
        
      },
      {
        type: "Button",
        props: {
          btnText: "Show overlay",
          elevation: "lg",
          size: "lg",
          textMode: true,
          clickEvent: function(){
            overlay3 = !overlay3;
            overlay3 = true;
            }
        }
      },
      {
        type: "Overlay", props: {
          value: overlay3,
          slotContent: {
            type: "Card", props: {
              title: "Overlay card slot", 
              subtitle: "Test", 
              description: "Lorem ipsum blah blah blah",
              hasImage: true,
              imgSrc: "https://images.artistrunwebsite.com/arwblog/bg_37311453262250.jpg?1453262251"
            }
          }
        }
      },
      {
        type: "Grid", props:{ // THis is a nested grid.
          gridElements: [
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              },
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              },
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              },
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              },
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              },
              {
                  type: "Button", props: {
                    btnText: "Click me"
                  } 
              }
            
            ],
            justify: "right"
        }
      },
      {
        type: "Card", 
        props: {
          title: "Card", 
          subtitle: "Test", 
          description: "Lorem ipsum blah blah blah",
          hasImage: true,
          imgSrc: "https://images.artistrunwebsite.com/arwblog/bg_37311453262250.jpg?1453262251",
          shaped: true
        }
      },
      {
        type: "List", props: {
          items: listItems1
        }
      },
      {
        type: "Tooltip", props: {
          slotContent: {
            type: "Button", props: {
              btnText: "Tooltip Button"
            }
          }
        }
      }
    ];
   
</script>

<style>
  
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  h3 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3em;
    text-align: center;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
   
  }

  @media (max-width: 640px) {
    h1{
      font-size: 3em;
    }
   
  }
  .tooltips{
    z-index: -1;
  }
  .overlays{
    z-index: 99;
  }
  .lists{
    z-index: -1;
  
    height: max-content;
  }
  .textfields{
    z-index: -1;
  }
  .my-grid{
    z-index: -1;
  }
</style>
<!-- The Tailwind component directly below should be imported into all
    your components that use tailwind-->
<Tailwindcss />


<main>
  <h1>Component Practice!</h1>
  <p class="px-24"> 1) In App.svelte you have a series of commented out components. It your job to 
  build the components such that App.svelte works with them uncommented, and they 
  look like vuetify ones.
  <br><br>
  
  2) For icons refer to <a href="https://github.com/RobBrazier/svelte-awesome">svelte-awesome</a>
   <Icon data={faThumbsUp}/>. Youll need to import icons into your components like at the top
   of this file.<br><br>

  3) Refer to <a href="https://vuetifyjs.com/en/components/api-explorer/">
  Vuetify</a> componets for design. Try to replicate. <br><br>

  
   
  4) Dont alter App.svelte. (Other than uncommenting the components) <br><br>
  
  5) Refer to the comments in App.svelte for futher instruction. <br><br>

  6) Use tailwind. <br><br>
   
  7) Have fun! <Icon data={beer}/>
   </p>
</main>


<!-- Here are some button declarations that your components
    should be able to satisfy.
    
    1) All buttons should have ripple effect when clicked
    
    3) btnText attribute is where the button's text goes-->

<h3>Buttons</h3>
<section class="mx-10 my-10 ">



 <Button 
  btnText="Large Primary"
  color="primary"
  size="xl"
  elevation="sm"
 />

<!-- Buttons can have different levels of elevation -->

 <Button 
  btnText="Block Secondary Raised High"
  color="secondary"
  size="block"
  elevation="lg"
 />

 <!--default color should be purple like vuetify buttons
      default size is md-->

 <Button
  btnText="Rounded"
  rounded={true} />

 <Button 
  btnText="Outline"
  outline={true} />
  
 
 <Button 
  btnText="Text Button"
  textMode={true} />

<!-- by default disabled is false. Buttons should be disableable-->
 
 <Button
  btnText="Disabled"
  disabled={true} />

<!-- put an icon in this button. No btnText-->

 <Button fab={true} 
    elevation="lg"
    iconData={comment}/>

    <Button fab={true} 
    elevation="sm"
    size="lg"
    iconData={comment}/>

   
  

</section>


<!-- Card declarations that your components
    should be able to satisfy-->
<h3>Cards</h3>
<section class="container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-2 mx-auto p-10">
 
<Card title="Vegeta"
          subtitle="Prince of Sayans"
          description="Lorem ipsum ....."
          hasImage={true}
          imgSrc="https://qph.fs.quoracdn.net/main-qimg-40ccab97c4b182082c3525bb34575a37.webp"
          elevation="lg"
          >
        
        </Card>

<Card title="Svelte"
          subtitle="Javascript Framework"
          description="Lorem ipsum ....."
          hasImage={true}
          imgSrc="https://i0.wp.com/programmingwithmosh.com/wp-content/uploads/2019/12/1_OJLglSTFZ1PbwpRG0U2xXA.png?ssl=1"
          elevation="sm"
          >
        
        </Card>

<!-- nesting Button in Card -->

<Card title="Card with buttons"
          subtitle="No Image"
          >

      <Button fab={true} 
        elevation="lg"
        iconData={comment}/>

        </Card>
 
 
  <Card title="Tailwind"
          subtitle="Design"
          description="Lorem ipsum ....."
          hasImage={true}
          shaped={true}
          imgSrc="https://pbs.twimg.com/profile_images/895274026783866881/E1G1nNb0.jpg"
          elevation="lg"
          >
        
        </Card>


      <!-- Come up with your own bonus card attribute for this one.
      Doesnt have to fit the vuetify design pattern. Could be animation, styling, etc-->  

<Card title="Bonus"
          subtitle="Your own bonus property"
          description="Lorem ipsum ....."
          hasImage={true}
          shaped={true}
          imgSrc="https://www.travelweek.ca/wp-content/uploads/2020/04/Travel-Edge-investing-50-million-in-signing-bonus-incentive-for-luxury-travel-advisors.jpg"
          bonus={true}
          >
        
        </Card>

</section>



<section>

  <!-- footer nav should be fixed to the bottom of the screen.
      has an items attribute for a list of string options, as well as a list of icon options
      Should dispatch the id of the clicked item on click
      Slot is for content below nav items -->


  <Footer on:click={(event)=>{
    // should be able to forward the id of the clicked object to App.svelte
    console.log(event.detail);
  }} items={navItems} color="primary" icons={navIcons}> </Footer>
  
</section>


<h3>Overlays</h3>
<Button 
          btnText="Show Overlay 1"
          color="primary"
          size="xl"
          elevation="sm"
          
          on:click={()=>{overlay1 = !overlay1}}
        /> 

<Button 
          btnText="Show overlay 2"
          color="primary"
          size="xl"
          elevation="sm"
          
          on:click={()=>{overlay2 = !overlay2}}
        /> 
<section class="grid grid-cols-2 my-2 overlays" >


  <div class="mx-4 h-64 relative bg-red-100 border-2 border-gray-700 shadow-md rounded-lg overlays">
 


  <Overlay absolute="{true}" 
        opacity="{.5}" 
        zIndex="{99}" 
        bind:value="{overlay1}" 
         > 
         <Button 
          btnText="Hide Overlay"
          color="primary"
          size="xl"
          elevation="sm"
          on:click={()=>{overlay1 = !overlay1}}
        />  
        
        </Overlay>
     
    
        
</div>

  

<div class="mx-4 z-0 h-64 relative bg-red-100 border-2 border-gray-700 shadow-md rounded-lg overlays" >

   
 

  <Overlay absolute="{false}" 
        opacity="{.2}" 
        zIndex="{99}" 
        bind:value="{overlay2}"
        
         >

      
        
         <Button 
          btnText="Hide Overlay"
          color="primary"
          size="xl"
          elevation="sm"
          on:click={()=>{overlay2 = !overlay2}}
          /> 

          <Card title="Svelte"
                subtitle="Javascript Framework"
                description="Lorem ipsum ....."
                hasImage={true}
                imgSrc="https://i0.wp.com/programmingwithmosh.com/wp-content/uploads/2019/12/1_OJLglSTFZ1PbwpRG0U2xXA.png?ssl=1"
                elevation="sm"
                
            ></Card>
        

        </Overlay>
        
</div >
</section>

<h3>Tooltips</h3>
<section class="my-4 py-4 px-4 mx-4 flex tooltips">

<!-- 

    Tooltip wraps around content that it is associated with. So give tooltip a
    default slot.

    Make open on hover the default and open on click set as default to false

-->
<Tooltip position="left"
          openOnClick={true}
          openOnHover={false}>
  <div class="mx-12" >left tooltip</div>
</Tooltip>

<Tooltip position="right">
  <div class="mx-12" >right tooltip</div>
</Tooltip>

<Tooltip position="bottom"
          openOnClick={true}
          openOnHover={true}>
  <div class="mx-12" >bottom tooltip</div>
</Tooltip>

<Tooltip position="top">
  <div class="mx-12" > top tooltip</div>
</Tooltip>





</section>

<h3>Lists</h3>
<div class="my-4 py-4 px-4 mx-4 lists">
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
	
  <List title={"List one"}
        items={listItems1}
        shaped={true} />

  <List title={"List one"}
        items={listItems1}
         />

   <List title={"List two"}
        twoLine={true}
        items={listItems2}
        rounded={true} />




</div>


<h3>Textfield</h3>
<section class="my-4 py-4 px-4 mx-4 textfields">
    <!-- A see Vuetify examples for this basic text input -->

    <Textfield placeHolder="Default text input" />
    <Textfield placeHolder="Filled" filled={true} />
    <Textfield placeHolder="Outlined" outlined={true} />

</section>

<h3>Grids</h3>
<section class="my-4 py-4 px-4 mx-4 my-grid">
  <!--
      Given an array of objects passed into gridElements, the Grid component should be
      able to create a responsive grid. In this case the gridElements parameter is the 
      array above declared as gridItems. The object properties in gridItems have the same
      names as the associated component attributes. Some of the components like cards and
      overlays should be able to render slot data if slot data is passed in via the object
      list. Hints: 
              1) use tailwind flex.
              2) for rendering components in slots, use <svelte:component>
              3) for redering nested grid, try <svelte:self>
        (these are just hints and other solutions are welcome!)
  -->

  <Grid gridElements={gridItems} alignment="center" justify="center" textAlign="center"/>

  
  
</section>

<br><br><br><br><br><br><br><br><br><br><br><br>

