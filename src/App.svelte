<script>
import Modal from './Modal.svelte'

let people = [
	{
		name: 'Yoshi', beltColor: 'black', age: 25, id: 1
	},{
		name: 'Mario', beltColor: 'orange', age: 45, id: 2
	},{
		name: 'Luigi', beltColor: 'brown', age: 35, id: 3
	}
];

const handleClick = (id) => {
	people = people.filter((person) => person.id !== id);
}

let num = 5;
</script>

<Modal />
<main>
	{#each people as person (person.id)}
		<div>
		<h4>{person.name}</h4>
		{#if person.beltColor === 'black'}
			<p><strong>Master ninja</strong></p>
		{/if}
		<p>{person.age} years old, {person.beltColor} belt</p>
		<button on:click={(e) => {handleClick(e, person.id)}}>delete</button>
		</div>
	{:else}
		<p>There no people to show</p>	
	{/each}
</main>

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

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>