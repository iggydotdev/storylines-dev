
<script>


	import Map from '../components/map.svelte';
	import Overlay from '../components/overlay.svelte';
	import Tabs from '../components/tabs/tabs.svelte';
	let position ;

	function getCoordinates() {
		if (navigator.geolocation) {
			return new Promise(function(resolve, reject) {
				navigator.geolocation.getCurrentPosition(resolve, reject);
			});
		} 
	}
	
	position = getCoordinates();
	



</script>

<svelte:head>
	<title>Storylines</title>
</svelte:head>

{#await position}
	<div>Loading...</div>
{:then data} 
	<Tabs/>
	<Map pos={data}/>
{:catch error}
<div>{error.message}</div>
{/await}
<slot></slot>



