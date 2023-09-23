<script>
	export let completed = false;
	export let title = '';
	export let id;

	export let toggleTodo = () => {};
</script>

<div class="todo">
	<div class="checkbox-wrapper-5">
		<div class="check">
			<input {id} type="checkbox" bind:checked={completed} on:change={() => toggleTodo(id)} />
			<label for={id} />
		</div>
	</div>
	<p class={completed ? 'checked' : ''}>{title}</p>
</div>

<style>
	.todo {
		display: flex;
		align-items: center;
		justify-content: flex-start;
		gap: 5em;
		width: 25%;
		margin-left: 5rem;
	}

	p {
		font-weight: bold;
		letter-spacing: 1px;
	}

	.checked {
		display: inline-block;
		position: relative;
		transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
	}

	.checked:after {
		content: '';
		position: absolute;
		display: block;
		width: 100%;
		height: 1.5px;
		box-shadow: 0 1px rgba(255, 255, 255, 0.6);
		margin-top: -0.6em;
		background: black;
		transform-origin: center left;
		animation: strikethrough 0.5s cubic-bezier(0.55, 0, 0.1, 1) 1;
		transition: transform 0.5s cubic-bezier(0.55, 0, 0.1, 1);
	}

	@keyframes strikethrough {
		from {
			transform: scaleX(0);
		}
		to {
			transform: scaleX(1);
		}
	}

	input[type='checkbox']:checked {
		background-color: #e9ecee;
		box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), inset 0px -15px 10px -12px rgba(0, 0, 0, 0.05),
			inset 15px 10px -12px rgba(255, 255, 255, 0.1);
		color: #99a1a7;
	}

	input[type='checkbox']:checked:after {
		content: '';
	}

	.checkbox-wrapper-5 .check {
		--size: 35px;

		position: relative;
		background: linear-gradient(90deg, rgb(154, 154, 221), rgb(77, 77, 230));
		line-height: 0;
		perspective: 400px;
		font-size: var(--size);
	}

	.checkbox-wrapper-5 .check input[type='checkbox'],
	.checkbox-wrapper-5 .check label,
	.checkbox-wrapper-5 .check label::before,
	.checkbox-wrapper-5 .check label::after,
	.checkbox-wrapper-5 .check {
		appearance: none;
		display: inline-block;
		border-radius: var(--size);
		border: 0;
		transition: 0.35s ease-in-out;
		box-sizing: border-box;
		cursor: pointer;
	}

	.checkbox-wrapper-5 .check label {
		width: calc(2.2 * var(--size));
		height: var(--size);
		background: #d7d7d7;
		overflow: hidden;
	}

	.checkbox-wrapper-5 .check input[type='checkbox'] {
		position: absolute;
		z-index: 1;
		width: calc(0.8 * var(--size));
		height: calc(0.8 * var(--size));
		top: calc(0.1 * var(--size));
		left: calc(0.1 * var(--size));
		background: linear-gradient(45deg, #dedede, #ffffff);
		box-shadow: 0 6px 7px rgba(0, 0, 0, 0.3);
		outline: none;
		margin: 0;
	}

	.checkbox-wrapper-5 .check input[type='checkbox']:checked {
		left: calc(1.3 * var(--size));
	}

	.checkbox-wrapper-5 .check input[type='checkbox']:checked + label {
		background: transparent;
	}

	.checkbox-wrapper-5 .check label::before,
	.checkbox-wrapper-5 .check label::after {
		content: '· ·';
		position: absolute;
		overflow: hidden;
		left: calc(0.15 * var(--size));
		top: calc(0.5 * var(--size));
		height: var(--size);
		letter-spacing: calc(-0.04 * var(--size));
		color: #9b9b9b;
		font-family: 'Times New Roman', serif;
		z-index: 2;
		font-size: calc(0.6 * var(--size));
		border-radius: 0;
		transform-origin: 0 0 calc(-0.5 * var(--size));
		backface-visibility: hidden;
	}

	.checkbox-wrapper-5 .check label::after {
		content: '●';
		top: calc(0.65 * var(--size));
		left: calc(0.2 * var(--size));
		height: calc(0.1 * var(--size));
		width: calc(0.35 * var(--size));
		font-size: calc(0.2 * var(--size));
		transform-origin: 0 0 calc(-0.4 * var(--size));
	}

	.checkbox-wrapper-5 .check input[type='checkbox']:checked + label::before,
	.checkbox-wrapper-5 .check input[type='checkbox']:checked + label::after {
		left: calc(1.55 * var(--size));
		top: calc(0.4 * var(--size));
		line-height: calc(0.1 * var(--size));
		transform: rotateY(360deg);
	}

	.checkbox-wrapper-5 .check input[type='checkbox']:checked + label::after {
		height: calc(0.16 * var(--size));
		top: calc(0.55 * var(--size));
		left: calc(1.6 * var(--size));
		font-size: calc(0.6 * var(--size));
		line-height: 0;
	}
</style>
