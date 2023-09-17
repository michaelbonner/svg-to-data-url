<script lang="ts">
	let svg = '';
	let encodedSvg = '';
	let svgBackground = '';

	function handleInput(event: any) {
		svg = event.target.value;
		encodedSvg = encodeURIComponent(svg);
		svgBackground = `url("data:image/svg+xml,${encodedSvg}")`;
	}
</script>

<h1 class="text-3xl">SVG to data url</h1>

<textarea
	placeholder="<svg>...</svg>"
	class="w-full h-64 border py-2 px-4"
	bind:value={svg}
	on:input={handleInput}
/>

{#if svg}
	<div class="grid gap-4">
		<div class="inline-flex justify-start">
			<div class="bg-gray-50 p-4">
				<div class="svg-display" style="background-image: {svgBackground}" />
			</div>
		</div>

		<div>
			<h2 class="font-bold">Encoded SVG</h2>
			<div class="max-w-full overflow-x-scroll py-2 px-4 bg-gray-50">
				<code class="break-all">{encodedSvg}</code>
			</div>
		</div>

		<div>
			<h2 class="font-bold">SVG Background</h2>
			<div class="max-w-full overflow-x-scroll py-2 px-4 bg-gray-50">
				<code class="break-all">{svgBackground}</code>
			</div>
		</div>
	</div>
{/if}

<style>
	.svg-display {
		width: 22px;
		height: 22px;
	}
</style>
