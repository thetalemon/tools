<script lang="ts">
	import InputRgba from '../../components/mix-blend-mode/inputRgba.svelte';
	import InputSlider from '../../components/mix-blend-mode/inputSlider.svelte';
	import BasicLayout from '../../components/layout/basicLayout.svelte';
	import MixBlendModeImg from '../../components/mix-blend-mode/mixBlendModeImg.svelte';
	import type { ImgOptions } from '../../components/mix-blend-mode/type';

	let imgSrc: string = 'Ak81Vc-kCf4';
	let text: ImgOptions = {
		red: 150,
		green: 200,
		blue: 255,
		alpha: 1,
		blendMode: 'normal',
		top: 240,
		left: 80,
		layer: 0
	};
	let mask: ImgOptions = {
		red: 10,
		green: 60,
		blue: 100,
		alpha: 1,
		blendMode: 'overlay',
		top: -24,
		left: -24,
		layer: 1
	};
</script>

<BasicLayout title="mix-blend-modeおためししすてむ">
	<div class="root">
		<h1>mix-blend-modeおためししすてむ</h1>
		<h2>画像設定</h2>
		<div>unsplashの画像ID: <input bind:value={imgSrc} /></div>
		<section>
			<h2>テキストの設定</h2>
			<div class="settings">
				<section>
					<h3>色</h3>
					<InputRgba
						bind:red={text.red}
						bind:green={text.green}
						bind:blue={text.blue}
						bind:alpha={text.alpha}
						bind:blendMode={text.blendMode}
					/>
				</section>
				<section>
					<h3>位置</h3>
					<InputSlider bind:value={text.top} text="上から" min={-120} max={400} />
					<InputSlider bind:value={text.left} text="左から" min={-400} max={400} />
					<InputSlider bind:value={text.layer} text="重ね順" min={0} max={100} />
				</section>
			</div>
		</section>
		<section>
			<h2>上レイヤー</h2>
			<div class="settings">
				<section>
					<h3>色</h3>
					<InputRgba
						bind:red={mask.red}
						bind:green={mask.green}
						bind:blue={mask.blue}
						bind:alpha={mask.alpha}
						bind:blendMode={mask.blendMode}
					/>
				</section>
				<section>
					<h3>位置</h3>
					<InputSlider bind:value={mask.top} text="上から" min={-120} max={400} />
					<InputSlider bind:value={mask.left} text="左から" min={-400} max={400} />
					<InputSlider bind:value={mask.layer} text="重ね順" min={0} max={100} />
				</section>
			</div>
		</section>
		<MixBlendModeImg {text} {mask} {imgSrc} />
	</div>
</BasicLayout>

<style lang="scss">
	.root {
		padding: 8px;
	}
	h2 {
		margin: 2rem 0 0 0;
	}
	h3 {
		margin: 0.25rem 0 0.25rem 0;
	}

	.settings {
		display: flex;
	}
</style>
