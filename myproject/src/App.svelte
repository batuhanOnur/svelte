<script>
import Modal from './Modal.svelte';
  
  let showModal = false;

  const toggleModal = () => {
    showModal = !showModal;
  }

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

<Modal message="Prop value" {showModal} on:click={toggleModal}/>


<main>
 <!-- Loops -->
  <button on:click|once={toggleModal}> OPEN MODAL</button>
  {#each people as person (person.id)}
   <div>
     <h4>{person.name}</h4>
     <p>{person.age} years old, {person.beltColor} belt.</p>
     <button on:click={ ()=> handleClick(person.id) }>delete</button>
   </div>
   {:else}
   <p> there are no people to show..</p>
  {/each}



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

