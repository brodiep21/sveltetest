<script>
 let first = 'B';
 let last  = 'Peif' ;
 $: fullname = `${first} ${last}`;
 let color = 'black';
//  import sus-fry.gif from './sus-fry.gif'
 let fry = '/sus-fry.gif';

 const handleClick = () => {
	color = 'orange';
 };

const input = (e) => {
	color = e.target.value ;
}
</script>

<main>
	<h1 style = "color: {color}">Hello {fullname}!</h1>
	<!-- <p style="color: {color}">{color}</p> -->
	<button on:click= {handleClick}>update belt color</button>
	<input type= "text" on:input= {input} bind:value={color}>
	<input type= "text" bind:value={first}>
	<input type= "text" bind:value={last}>
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