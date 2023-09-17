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

<textarea class="w-full h-64 border" bind:value={svg} on:input={handleInput} />

{#if svg}
	<div class="bg-gray-50 p-4 inline-flex my-2">
		<div class="svg-display" style="background-image: {svgBackground}" />
	</div>

	<div class="my-2">
		<h2>Encoded SVG</h2>
		<pre>{encodedSvg}</pre>
	</div>

	<div class="my-2">
		<h2>SVG Background</h2>
		<pre>{svgBackground}</pre>
	</div>
{/if}

<style>
	.svg-display {
		width: 22px;
		height: 22px;
	}
</style>
