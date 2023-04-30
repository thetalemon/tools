<script lang="ts">
	import InputSlider from '../components/inputSlider.svelte';
	import MixBlendMode from '../components/mixBlendMode.svelte';
	export let text: string;

	export let red = 0;
	export let green = 0;
	export let blue = 0;
	export let alpha = 0;
	export let blendMode = 'normal';
</script>

<h2>{text}</h2>
<MixBlendMode bind:selected={blendMode} />
<ul>
	<li>
		<InputSlider bind:value={red} text="red" />
	</li>
	<li>
		<InputSlider bind:value={green} text="green" />
	</li>
	<li>
		<InputSlider bind:value={blue} text="blue" />
	</li>
	<li>
		<InputSlider bind:value={alpha} text="alpha" />
	</li>
</ul>

<style lang="scss">
	ul {
		list-style: none;
		li {
			display: flex;
			margin: 8px 0;
		}
	}
</style>
