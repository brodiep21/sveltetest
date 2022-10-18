<script>
    import {createEventDispatcher} from 'svelte';
let dispatch = createEventDispatcher();
let name;
let color;
let age;
let skills = [];

const handleSubmit = () => {
    const person = {
        name,
        color,
        age,
        skills,
        id: Math.random()
    }
    dispatch('addPerson', person);
}
</script>

<!-- prevents page from refreshing when you submit -->
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name" bind:value={name}>
    <!-- <input type="text" placeholder="Belt Color" bind:value={color}> -->
    <input type="number" placeholder="Age" bind:value={age}>
    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting">Fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">Sneaking<br>
    <input type="checkbox" bind:group={skills} value="shooting">Shooting<br>
    <label>Belt Color:</label>
    <select bind:value={color}>
        <option value="Black">Black</option>
        <option value="Green">Green</option>
        <option value="Orange">Orange</option>
        <option value="Purple">Purple</option>
    </select>

    <button>Add Person</button>
</form>

<style>

</style>