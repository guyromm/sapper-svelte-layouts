<script>
 import { goto } from '@sapper/app';
 import {Switcher,Box} from './layout';
 export let segment;
 const pagenames = ['grid','stack','box','bracket','cluster','sidebar','switcher','cover','frame','reel','imposter'];
 const navpages = {}; // 'home (the grid)':{url:'/'}
 const l = console.log;
 for (const page of pagenames)
     navpages[page]={};
 navpages.grid={url:'/'};
 let cursegment;
 $: {
     cursegment = (segment || 'grid');
     l('cursegment:',cursegment);     
    }
 const handleKey = (e) => {
     let pos = pagenames.indexOf(cursegment);
     let idx=0;
     if (e.key==='n')
	 idx=pos+1;
     else if (e.key==='p')
	 idx=pos-1;
     else if (e.key==='h')
	 idx=0; //pos*-1;
     else
	 idx=pos;
     if (idx>=pagenames.length) idx=0;
     else if (idx<0) idx=pagenames.length-1;
     let nsegment=pagenames[idx];     
     l(e,'pos',pos,'keyup',e.key,idx,cursegment,'=>',nsegment,nsegment===cursegment);
     if (nsegment!==cursegment) goto(navpages[nsegment].url?
				     navpages[nsegment].url:
				     nsegment);
     }
</script>
<svelte:window on:keyup={handleKey}/>
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

    a span { color:white; } 
</style>
<nav>
    <Switcher>
	{#each Object.entries(navpages) as [label,opts]}
	    <Box><a
		     aria-current={((segment!==undefined && segment===opts.url) ||
				cursegment===label ||
				(segment===undefined && opts.url==='.'))?"page":undefined}
		   href={opts.url?opts.url:label}
		   {...opts.attrs}
		><span>{label}</span></a></Box>
	{/each}
    </Switcher>
</nav>
