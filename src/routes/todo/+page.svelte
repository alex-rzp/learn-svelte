<script>
	let todos = [];
	let todo = '';

	function addTodo() {
		let newTodo = {
			id: new Date().getTime(),
			text: todo,
			completed: false
		};
		todos = [...todos, newTodo];
		todo = '';
	}

	function removeTodo(id) {
		todos = todos.filter((t) => t.id !== id);
	}
</script>

<section class="flex flex-col items-center">
	<h1 class="text-3xl mb-5">Todos</h1>

	<form class="w-full flex" on:submit|preventDefault={addTodo}>
		<input class="border p-2 w-full" placeholder="Create new todo" type="text" bind:value={todo} />
		<button type="submit" class="bg-blue-500 text-white px-4 py-2 hover:bg-blue-400">Create</button>
	</form>

	<ul class="w-full mt-5">
		{#each todos as { id, text, completed } (id)}
			<li class="w-full border-b border-gray-200 py-2 px-4 flex items-center justify-between">
				<div>
					<input class="mr-2" type="checkbox" bind:checked={completed} />
					<span class="text-gray-600 {completed ? 'line-through' : ''}">{text}</span>
				</div>

				<button
					class="bg-red-500 text-white px-4 py-2 hover:bg-red-400"
					on:click={() => removeTodo(id)}>Delete</button
				>
			</li>
		{/each}
	</ul>
</section>
