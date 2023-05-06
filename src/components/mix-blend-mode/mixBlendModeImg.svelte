<script lang="ts">
	import type { ImgOptions } from './type';

	export let imgSrc: string;
	export let text: ImgOptions;
	export let mask: ImgOptions;
</script>

<div
	class="root"
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

<style lang="scss">
	.root {
		display: flex;
		justify-content: center;
		margin: 48px;
		margin-bottom: 500px;
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
