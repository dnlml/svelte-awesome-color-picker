<script lang="ts">
	export let wrapper: HTMLElement;
	export let isOpen: boolean;
	export let isPopup: boolean;
	/* svelte-ignore unused-export-let */
	export let toRight: boolean;
</script>

<div class="wrapper" bind:this={wrapper} class:isOpen class:isPopup>
	<slot />
</div>

<style>
	div {
		padding: 8px 5px 5px 8px;
		background-color: white;
		margin: 0 10px 10px;
		border: 1px solid black;
		border-radius: 12px;
		display: none;
	}
	.isOpen {
		display: block;
	}
	@media (min-width: 768px) {
		.isOpen {
			display: grid;
			grid-template:
				'picker . . a11y'
				'input input input a11y';
		}
	}

	div :global(.picker) {
		grid-area: picker;
	}

	div :global(.text-input) {
		grid-area: input;
	}

	div :global(.a11y-notice) {
		grid-area: a11y;
		margin: 0 4px 0 6px;
	}

	div :global(.slider-wrapper) {
		margin-left: 5px;
	}

	.isPopup {
		position: absolute;
		top: 25px;
		z-index: 2;
	}
</style>
