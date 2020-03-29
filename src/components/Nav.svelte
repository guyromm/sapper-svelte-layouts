<script>
 import {Switcher,Box} from './layout';
 export let segment;
 const navpages = {'home (the grid)':{url:'.'}};
 for (const page of ['stack','box','bracket','cluster','sidebar','switcher','cover','frame','reel','imposter'])
     navpages[page]={};
</script>

<style>

:global(a[target="_blank"], a[target="blank"]) {
color:red;
}
 nav {
		border-bottom: 1px solid rgba(255,62,0,0.1);
		font-weight: 300;
		padding: 0 1em;
	}

	ul {
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		float: left;
	}

	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		background-color: rgb(255,62,0);
		display: block;
		bottom: -1px;
	}

/*	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}*/
    a span { color:white; } 
</style>
<nav>
    <Switcher>
	{#each Object.entries(navpages) as [label,opts]}
	    <Box><a
		     aria-current={((segment!==undefined && segment===opts.url) ||
				segment===label ||
				(segment===undefined && opts.url==='.'))?"page":undefined}
		   href={opts.url?opts.url:label}
		   {...opts.attrs}
		><span>{label}</span></a></Box>
	{/each}
    </Switcher>
</nav>
