<script lang="ts">
	export let value: number = 0;
	export let text: string;
	export let min: number = 0;
	export let max: number = 255;
	export let step: number = 1;
</script>

<div class="root">
	<div class="label">{text}</div>
	<div class="slider"><input type="range" bind:value {min} {max} {step} /></div>
	<div class="num"><input type="number" bind:value {min} {max} {step} /></div>
</div>

<style lang="scss">
	.root {
		display: flex;
		.label {
			width: 5rem;
		}
		.num {
			width: 7rem;
		}
		.slider {
			width: 10rem;
		}
		div {
			margin: 0.25rem 0;
		}
		input {
			border-radius: 8px;
		}
	}
</style>
