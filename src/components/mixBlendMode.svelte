<script lang="ts">
	export let selected: string;

	const MIX_BLEND_MODE_OPTION: string[] = [
		'normal',
		'multiply',
		'screen',
		'overlay',
		'darken',
		'lighten',
		'color-dodge',
		'color-burn',
		'hard-light',
		'soft-light',
		'difference',
		'exclusion',
		'hue',
		'saturation',
		'color',
		'luminosity'
	];
</script>

<p>
	<span> mix-blend-mode: </span>
	<select bind:value={selected}>
		{#each MIX_BLEND_MODE_OPTION as item}
			<option value={item}>
				{item}
			</option>
		{/each}
	</select>
</p>

<style lang="scss">
	p {
		margin: 0;
	}
	span {
		display: inline-block;
		margin-right: 8px;
	}
	select {
		height: 24px;
		width: 120px;
		border-radius: 8px;
		margin: 0.25rem 0;
	}
</style>
