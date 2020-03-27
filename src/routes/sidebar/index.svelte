<script>
 import Presentation from '../../components/Presentation.svelte';
 import {Sidebar, Cover, Box,Stack } from '../../components/layout';
</script>
<style>
    :global([slot]) {
    display: contents;
    }
</style>

<svelte:head>
	<title>sidebar home</title>
</svelte:head>

<Cover>
    <Presentation>
	
	<a slot="title" href="https://every-layout.dev/layouts/sidebar/" target="blank"><h5>Sidebar</h5></a>
	<Sidebar>
	    
	    <div slot="sidebar">
		<Box padding="s-2" color="white">
		    <Stack splitAfter="1">
			<p>A</p>
			<p>B</p>
		    </Stack>
		</Box>
	    </div>
	    
	    <div slot="not-sidebar">
		<Box color="white">
		    <p>Main Content</p>
		</Box>
	    </div>
	    
	</Sidebar>
    </Presentation>
</Cover>
