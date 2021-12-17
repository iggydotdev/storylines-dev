<script>

	import * as L from 'leaflet';
	import "leaflet-providers";
	import 'leaflet/dist/leaflet.css';

	export let pos;

	let map;


	function addUser(map,coords, options) {
		L.circle([coords.latitude, coords.longitude], options).addTo(map);
	}
	function addMarker(map,coords, options) {
		L.marker([coords.latitude, coords.longitude], options).addTo(map);
	}

	function createMap (container) {
		let m = new L.Map(container, {
				center: new L.LatLng(pos.coords.latitude,pos.coords.longitude),
				zoom: 18
			});
		
		L.tileLayer.provider('Stamen.Toner').addTo(m);
		

		addUser(m,{latitude: pos.coords.latitude, longitude: pos.coords.longitude},{
			color: 'red',
			fillColor: '#f03',
			fillOpacity: 0.5,
			radius: 500,	
		});

		addMarker(m,{latitude: pos.coords.latitude, longitude: pos.coords.longitude});

		addUser(m,{latitude: -27.404916, longitude: 152.929174},{
			color: 'royalblue',
			fillColor: '#312232',
			fillOpacity: 0.5,
			radius: 500,
			weight: 1, 
		});
		
		return m;  

	}

	function mapAction(container) {
		map = createMap(container);
		return {
			destroy: () => {
				map.remove();
			},
		};
	}
</script>

<div class="map" use:mapAction />

<style>

	.map {
		height: 100vh;
		z-index: -1;
		position: absolute;
		width: 100%;
	}

	</style>