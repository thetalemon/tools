<script lang="ts">
	import InputRgba from '../components/inputRgba.svelte';

	export let imgSrc: string = 'Ak81Vc-kCf4';
	let redText = 0;
	let greenText = 0;
	let blueText = 0;
	let alphaText = 0;
	let blendModeText = 'normal';
	let redOverRay = 0;
	let greenOverRay = 0;
	let blueOverRay = 0;
	let alphaOverRay = 0;
	let blendModeOverRay = 'normal';
</script>

<div style="--overray-blend-mode: {blendModeOverRay}">
	<div>optional: 画像ID <input bind:value={imgSrc} /></div>

	<InputRgba
		text={'テキスト色'}
		bind:red={redText}
		bind:green={greenText}
		bind:blue={blueText}
		bind:alpha={alphaText}
		bind:blendMode={blendModeText}
	/>
	<InputRgba
		text={'オーバーレイ色'}
		bind:red={redOverRay}
		bind:green={greenOverRay}
		bind:blue={blueOverRay}
		bind:alpha={alphaOverRay}
		bind:blendMode={blendModeOverRay}
	/>

	<div class="contentWrapper">
		<div class="imgWrapper">
			<p class="text">Welcome</p>
			<img src={`https://source.unsplash.com/${imgSrc ? imgSrc : 'Ak81Vc-kCf4'}`} alt="画像" />
		</div>
	</div>
</div>

<style lang="scss">
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
				right: 16px;
				bottom: 16px;
				margin: 0;
				z-index: 0;
				line-height: 1;
				color: rgba(150, 200, 255);
				mix-blend-mode: screen;
			}

			&::before {
				position: absolute;
				display: block;
				width: calc(100% + 48px);
				height: calc(100% + 48px);
				content: '';
				left: -24px;
				top: -24px;
				background: rgba(10, 60, 100);
				z-index: 1;
				mix-blend-mode: var(--overray-blend-mode);
			}
		}
	}
</style>
