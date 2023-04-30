<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let filterText = '';

	const inputDispatch = createEventDispatcher();

	function handleFilterChange(event: any) {
		filterText = event.target.value;
		inputDispatch('filterChanged', { filterText });
	}
</script>

<input
	type="text"
	class="filter-input"
	placeholder="Filter by name"
	bind:value={filterText}
	on:input={handleFilterChange}
/>

<style>
	.filter-input {
		padding: 0.9rem 1rem;
		margin: 8px 0;
		box-sizing: border-box;
		border: 0.1rem solid #ccc;
		border-radius: 0.2rem;
		background-color: #fff;
		font-size: 1rem;
	}

	.filter-input:focus {
		border: 0.2rem solid #4caf50;
	}
</style>
