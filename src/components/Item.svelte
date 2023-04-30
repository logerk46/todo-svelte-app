<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let id: number;
	export let name: string;
	export let description: string;

	const deleteDispatch = createEventDispatcher();

	function onDelete(): void {
		deleteDispatch('delete', { id });
	}
</script>

<div class="card">
	<h5>{name}</h5>
	<p>{description}</p>
	<button on:click={onDelete}>Delete</button>
</div>

<style>
	.card {
		display: flex;
		flex-direction: column;
		padding: 1.2rem;
		background-color: #fff;
		box-shadow: 0px 0.1rem 0.4rem rgba(0, 0, 0, 0.1);
		border-radius: 0.8rem;
	}

	h5 {
		font-size: 1.2rem;
		font-weight: 500;
		margin-block-start: 0rem;
		margin-block-end: 0rem;
		color: #333;
	}

	p {
		height: 6rem;
		max-width: 100%;
		-webkit-line-clamp: 4;
		-webkit-box-orient: vertical;
		font-size: 1rem;
		color: #777;
		margin-block: 0.8rem;
		display: -webkit-box;
		overflow: hidden;
		text-overflow: ellipsis;
		line-height: 1.5;
	}

	button {
		align-self: flex-end;
		background-color: #f44336;
		width: fit-content;
		color: #fff;
		font-size: 1rem;
		font-weight: 500;
		border: none;
		border-radius: 0.2rem;
		padding: 0.4rem 1.2rem;
		cursor: pointer;
		transition: background-color 0.3s ease;
	}

	button:hover {
		background-color: #e53935;
	}
</style>
