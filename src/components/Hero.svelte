<script>
	import { onMount } from 'svelte';
	import { Map } from 'mapbox-gl';
	import 'mapbox-gl/dist/mapbox-gl.css';

	let map;
	let mapContainer;
	let lng, lat, zoom;

	lng = -71.224518;
	lat = 42.213995;
	zoom = 9;

	onMount(() => {
		const initialState = { lng: lng, lat: lat, zoom: zoom };

		map = new Map({
			container: mapContainer,
			accessToken: 'TOKEN',
			style: `mapbox://styles/mapbox/outdoors-v11`,
			center: [initialState.lng, initialState.lat],
			zoom: initialState.zoom
		});
	});
</script>

<section class="text-stone-950">
	<div
		class="container mx-auto flex flex-col items-center px-4 py-16 text-center md:py-32 md:px-10 lg:px-32 xl:max-w-3xl"
	>
		<h1 class="text-4xl font-bold leadi sm:text-5xl">MapBox Playground</h1>

		<div class="map" bind:this={mapContainer} />

		<div class="flex flex-wrap justify-center">
			<button class="px-8 py-3 m-2 text-lg border rounded text-stone-950 border-gray-700"
				>Learn more</button
			>
		</div>
	</div>
</section>

<style>
	.map {
		width: 500px;
		height: 500px;
		margin: 2rem;
	}
</style>
