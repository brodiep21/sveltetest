<script>
	import Modal from './Modal.svelte';
 let first = 'B';
 let last  = 'Peif' ;
 $: fullname = `${first} ${last}`;
 let people = [
	{name: 'Brodie', color: 'orange', age: 32, id: 1},
	{name: 'Conner', color: 'blue', age: 31, id: 2},
	{name: 'Eli', color: 'green', age: 31, id: 3},
	{name: 'Hailey', color: 'yellow', age: 29, id: 4},
	{name: 'Denzell', color: 'turquoise', age: 42, id: 5},
 ];
 let color = 'black';
//  import sus-fry.gif from './sus-fry.gif'
 let fry = '/sus-fry.gif';
 
 //filter through the array - checks the id of the person, if the person.id is not equal to id passed into the function, return true and keep that item in the array.
 const handleClick = (id) => {
	people = people.filter((person) => person.id != id);
 }
 let num = 14;
 //takes the value of the input and updates it
const typingVal = (e) => {
	color = e.target.value ;
}
</script>
<Modal/>
<!-- {#if num > 20}
<p>Greater than 20</p>
{:else if num > 5}
<p>Greater Than 5</p>
{/if} -->
<main>
	<h1 style = "color: {color}">Hello {fullname}!</h1>
	<!-- <p style="color: {color}">{color}</p> -->
	<!-- <button on:click= {handleClick}>update belt color</button> -->
	<input type= "text" on:input= {typingVal} bind:value={color}>
	<input type= "text" bind:value={first}>
	<input type= "text" bind:value={last}>
	<div>
		{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.age} years old, {person.color} belt.</p>
			//wrap the event in the object so that it doesn't automatically run when the each loop is ran
			<button on:click={() => handleClick(person.id)}>Delete</button>
		</div>
		{:else}
		<p>There are no people to show...</p>
		{/each}
	</div>
	<br><img {fry} alt="fry squinting">
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>