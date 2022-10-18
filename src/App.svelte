<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';
	import PopUpError from './PopUpError.svelte'
//  let first = 'B';
//  let last  = 'Peif' ;
//  $: fullname = `${first} ${last}`;
 let showModal = false;
 let showPopUp = false;
 let people = [
	{name: 'Brodie', color: 'orange', age: 32, skills:[], id: 1},
	{name: 'Conner', color: 'blue', age: 31,skills:[],id: 2},
	{name: 'Eli', color: 'green', age: 31,skills:[], id: 3},
	{name: 'Hailey', color: 'yellow', age: 29,skills:[], id: 4},
	{name: 'Denzell', color: 'turquoise', age: 42,skills:[], id: 5},
 ];
 let color = 'black';
//  import sus-fry.gif from './sus-fry.gif'
 let fry = '/sus-fry.gif';
 
 //filter through the array - checks the id of the person, if the person.id is not equal to id passed into the function, return true and keep that item in the array.
 const handleClick = (id) => {
	people = people.filter((person) => person.id != id);
 };
 let num = 14;
 //takes the value of the input and updates it
const typingVal = (e) => {
	color = e.target.value ;
};
const toggleModal = () => {
	showModal = !showModal;
};
const togglePopUp = () => {
	showPopUp = !showPopUp;
}
const addPerson = (e) => {
	let person = e.detail;
		people = [person, ...people];
		showModal = false;
};
</script>
<!-- <Modal/> -->

<Modal {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson}/>
</Modal>
<PopUpError {showPopUp} on:click={togglePopUp}/>
<main>
	<!-- <h1 style = "color: {color}">Hello {fullname}!</h1>
	<input type= "text" on:input= {typingVal} bind:value={color}>
	<input type= "text" bind:value={first}>
	<input type= "text" bind:value={last}> -->
	<div>
		<button on:click={toggleModal}>Open Modal</button> 
		{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			<p>{person.age} years old, {person.color} belt.
				{#if person.skills} 
				<div class="skills">
						{#each person.skills as skill}
						<li class="skill">{skill}
						</li>
						{/each}
				</div>
				{/if}
			</p>
			<!-- //wrap the event in the object so that it doesn't trigger automatically when the each loop is ran -->
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