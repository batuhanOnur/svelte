<script>
import Modal from './Modal.svelte';
  // let firstName = "Batuhan";
  // let lastName = "Onur";
  // let beltColor = "black";
  
  // $: fullName = `${firstName} ${lastName}`;
  // $: console.log(beltColor);

  // const handleClick = () => {
  //   beltColor = 'orange'
  // }

  // const handleInput = (e) => {
  //   beltColor = e.target.value; 
  // }

  let people = [
    {name: 'yoshi', beltColor:'black', age:25, id:1},
    {name: 'mario', beltColor:'orange', age:32, id:2},
    {name: 'luigi', beltColor:'brown', age:44, id:3},
  ];


  const handleClick = (id) => {
     people = people.filter((person)=> person.id != id)
  }

  let num = 3;
</script>

<Modal />

{#if num > 20}
<p> greater than 20</p>

{:else if num > 5}
<p> greater than 5</p>

{:else}
<p> not greater than 5</p>
{/if}



<main>
  <!-- <h1>Hello {name}!</h1>
  <p style="color: {beltColor}">{beltColor} belt</p>
  <button on:click={handleClick}>update belt color</button>
  <!-- <input type="text" on:input={handleInput} value={beltColor}/>
   -->

  <!-- Reactive Values -->

  <!-- <p>{fullName} {beltColor}-belt</p>

  <input type="text" bind:value={firstName}> 
  <input type="text" bind:value={lastName}> 
  <input type="text" bind:value={beltColor}>  -->
  
  <!-- Loops -->

  {#each people as person (person.id)}
   <div>
     <h4>{person.name}</h4>
     <p>{person.age} years old, {person.beltColor} belt.</p>
     <button on:click={ ()=> handleClick(person.id) }>delete</button>
   </div>
   {:else}
   <p> there are no people to show..</p>
  {/each}
  
</main>


<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }


  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

