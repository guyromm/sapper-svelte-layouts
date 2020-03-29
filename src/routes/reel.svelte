<script>
 import { Cover,
	Stack,
	Bracket,
	Cluster,
	Sidebar,
	Switcher,
	Frame,
	Reel,
	Imposter,
	Grid,
	Box} from '../components/layout';
 import {loremIpsum} from "lorem-ipsum";  
 import Presentation from '../components/Presentation.svelte';
</script>
<div style="max-width: 48rem;min-height:26rem;">
    {loremIpsum({count:10})}
    <Reel itemWidth="s4">
	{#each [...Array(10).keys()] as i}
	    <img
		src="favicon.png"
		alt="favicon {i}"
		title={i}/>
	{/each}
    </Reel>
    {loremIpsum({count:10})}
</div>


