<script>
 import {Cover,Box} from '../components/layout';
 import {loremIpsum} from "lorem-ipsum";  
</script>

<Cover minHeight="10vh">
	    <div slot="above">
		<Box padding="zero">{loremIpsum({count:5})}</Box>
	    </div>
	    <Box padding="s1">{loremIpsum({count:50})}</Box>
	    <div slot="below">
		<Box padding="zero">{loremIpsum({count:5})}</Box>
	    </div>
	</Cover>
