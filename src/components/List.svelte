<script lang="ts">
	import Item from './Item.svelte';
	import Filter from './Filter.svelte';

	let searchValue = '';

	let todos = [
		{
			id: 1,
			name: 'Todo 1',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur risus vitae nisl euismod facilisis. Quisque ornare felis diam, nec vestibulum justo tempor sit amet. Etiam sed semper leo. Vivamus nec lacus lectus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin accumsan sagittis turpis sed facilisis. Curabitur porta lorem dignissim, lacinia diam vel, luctus est. Pellentesque vel lectus eu nisi tincidunt semper sed vitae neque.'
		},
		{
			id: 2,
			name: 'Todo 2',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur risus vitae nisl euismod facilisis. Quisque ornare felis diam, nec vestibulum justo tempor sit amet. Etiam sed semper leo. Vivamus nec lacus lectus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin accumsan sagittis turpis sed facilisis. Curabitur porta lorem dignissim, lacinia diam vel, luctus est. Pellentesque vel lectus eu nisi tincidunt semper sed vitae neque.'
		},
		{
			id: 3,
			name: 'Todo 3',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur risus vitae nisl euismod facilisis. Quisque ornare felis diam, nec vestibulum justo tempor sit amet. Etiam sed semper leo. Vivamus nec lacus lectus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin accumsan sagittis turpis sed facilisis. Curabitur porta lorem dignissim, lacinia diam vel, luctus est. Pellentesque vel lectus eu nisi tincidunt semper sed vitae neque.'
		},
		{
			id: 4,
			name: 'Todo 4',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam efficitur risus vitae nisl euismod facilisis. Quisque ornare felis diam, nec vestibulum justo tempor sit amet. Etiam sed semper leo. Vivamus nec lacus lectus. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin accumsan sagittis turpis sed facilisis. Curabitur porta lorem dignissim, lacinia diam vel, luctus est. Pellentesque vel lectus eu nisi tincidunt semper sed vitae neque.'
		}
	];

	$: filteredTodos = todos.filter(
		(item) => item.name.toLocaleLowerCase().indexOf(searchValue) !== -1
	);

	function handleDelete({ detail }: CustomEvent<{ id: number }>): void {
		todos = todos.filter((todo) => todo.id !== detail.id);
	}

	function handleFilterByName({ detail }: CustomEvent<{ filterText: string }>): void {
		searchValue = detail.filterText;
	}
</script>

<Filter on:filterChanged={handleFilterByName} />
<div class="cards">
	{#each filteredTodos as item (item.id)}
		<Item {...item} on:delete={handleDelete} />
	{/each}
</div>

<style>
	.cards {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		gap: 1rem;
	}
</style>
