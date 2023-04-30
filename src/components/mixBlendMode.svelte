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

<select bind:value={selected}>
	{#each MIX_BLEND_MODE_OPTION as item}
		<option value={item}>
			{item}
		</option>
	{/each}
</select>
