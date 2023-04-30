<script lang="ts">
	import InputSlider from '../components/inputSlider.svelte';
	import MixBlendMode from '../components/mixBlendMode.svelte';

	export let red = 0;
	export let green = 0;
	export let blue = 0;
	export let alpha = 0;
	export let blendMode = 'normal';
</script>

<div>
	<MixBlendMode bind:selected={blendMode} />
</div>
<div>
	<InputSlider bind:value={red} text="red" />
</div>
<div>
	<InputSlider bind:value={green} text="green" />
</div>
<div>
	<InputSlider bind:value={blue} text="blue" />
</div>
<div>
	<InputSlider bind:value={alpha} text="alpha" min={0} max={1} step={0.1} />
</div>
