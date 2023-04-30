<script lang="ts">
	export let value: number = 0;
	export let text: string;
</script>

<div class="root">
	<div>{text}:</div>
	<div><input type="range" bind:value min="0" max="255" /></div>
	<div><input type="number" bind:value min="0" max="255" /></div>
</div>

<style lang="scss">
	.root {
		display: flex;
		div {
			width: 150px;
		}
		input {
			border-radius: 6px;
		}
	}
</style>
