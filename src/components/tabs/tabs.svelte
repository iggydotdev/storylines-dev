<script>
	import Tab from './tab.svelte';
	import TabPanel from './tabPanel.svelte';	
	
	export let data;


</script>

<div>
	<!-- {#each data as tab} -->
		<Tab><button>X</button></Tab>
	<!-- {/each} -->
</div>

<div>
	<!-- {#each data as tab} -->
		<TabPanel>
			test
		</TabPanel>
	<!-- {/each} -->

</div>