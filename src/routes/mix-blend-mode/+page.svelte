<script lang="ts">
	import InputRgba from '../../components/mix-blend-mode/inputRgba.svelte';
	import InputSlider from '../../components/mix-blend-mode/inputSlider.svelte';
	import BasicLayout from '../../components/layout/basicLayout.svelte';

	export let imgSrc: string = 'Ak81Vc-kCf4';
	let text = {
		red: 150,
		green: 200,
		blue: 255,
		alpha: 1,
		blendMode: 'normal',
		top: 240,
		left: 80,
		layer: 0
	};
	let mask = {
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

<BasicLayout>
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

		<div
			class="contentWrapper"
			style="
    --text-blend-mode: {text.blendMode}; 
    --text-top: {text.top}px; --text-left: {text.left}px; 
    --text-red: {text.red}; --text-green: {text.green}; --text-blue: {text.blue}; --text-alpha: {text.alpha}; 
    --text-z-index: {text.layer};
    --mask-blend-mode: {mask.blendMode}; 
    --mask-top: {mask.top}px; --mask-left: {mask.left}px; 
    --mask-red: {mask.red}; --mask-green: {mask.green}; --mask-blue: {mask.blue}; --mask-alpha: {mask.alpha};
    --mask-z-index: {mask.layer};"
		>
			<div class="imgWrapper">
				<p class="text">Welcome</p>
				<img src={`https://source.unsplash.com/${imgSrc ? imgSrc : 'Ak81Vc-kCf4'}`} alt="画像" />
			</div>
		</div>
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
	.contentWrapper {
		display: flex;
		justify-content: center;
		margin: 48px;
		.imgWrapper {
			position: relative;
			margin: 24px;
			img {
				width: 500px;
			}
			.text {
				display: block;
				position: absolute;
				font-size: 88px;
				font-weight: 700;
				top: var(--text-top);
				left: var(--text-left);
				margin: 0;
				z-index: var(--text-z-index);
				line-height: 1;
				color: rgba(var(--text-red), var(--text-green), var(--text-blue), var(--text-alpha));
				mix-blend-mode: var(--text-blend-mode);
			}

			&::before {
				position: absolute;
				display: block;
				width: calc(100% + 48px);
				height: calc(100% + 48px);
				content: '';
				top: var(--mask-top);
				left: var(--mask-left);
				background: rgba(var(--mask-red), var(--mask-green), var(--mask-blue), var(--mask-alpha));
				z-index: var(--mask-z-index);
				mix-blend-mode: var(--mask-blend-mode);
			}
		}
	}
</style>
