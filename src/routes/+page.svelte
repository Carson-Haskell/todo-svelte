<script>
	import Todo from '../components/Todo.svelte';

	let todos = [
		{
			title: 'Add first todo',
			completed: false,
			id: 1
		}
	];

	let newTodo = '';

	const addTodo = (e) => {
		todos = [...todos, { title: newTodo, completed: false, id: todos.length + 1 }];
		newTodo = '';
	};

	const toggleTodo = (id) => {
		todos = todos.map((todo) => (todo.id === id ? { ...todo, completed: !todo.completed } : todo));
	};
</script>

<div class="container">
	<h1>TODOS</h1>
	<form class="todo-form" on:submit|preventDefault={addTodo}>
		<input type="text" id="todo" placeholder="New todo..." bind:value={newTodo} />
		<button class="btn">Add todo</button>
	</form>
	<div class="todos">
		{#each todos as todo}
			<Todo completed={todo.completed} title={todo.title} id={todo.id} {toggleTodo} />
		{/each}
	</div>
</div>

<style>
	h1 {
		font-weight: bold;
		letter-spacing: 3px;
	}

	.container {
		margin-top: 2rem;
	}

	.container,
	.todo-form {
		display: flex;
		align-items: center;
		flex-direction: column;
		justify-content: center;
	}

	.todo-form {
		gap: 2em;
	}

	input[type='text'] {
		width: 95%;
		height: 1.5rem;
		border-radius: 5px;
		border: 2px solid rgb(77, 77, 230);
		padding-left: 5%;
		transition: border-color 0.5s;
	}

	input[type='text']:hover {
		border-color: black;
	}

	.btn {
		border: none;
		border-radius: 20px;
		background: linear-gradient(90deg, rgb(154, 154, 221), rgb(77, 77, 230));
		padding: 1em 0;
		width: 100%;
		cursor: pointer;
		transition: all 0.5s;
		color: white;
	}

	.btn:hover {
		transform: scale(1.1);
		border-radius: 10px;
	}

	.btn:active {
		transform: scale(0.9);
	}

	.todos {
		margin-top: 5rem;
		width: 100vw;
		display: flex;
		flex-direction: column;
		gap: 2rem;
		overflow: scroll;
		align-items: center;
		height: 60vh;
	}
</style>
