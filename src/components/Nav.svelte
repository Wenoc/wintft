<script>
	export let segment;
	import NavBlogItem from './NavBlogItem.svelte'
	import { onMount } from 'svelte';
	let isHover = false;
	
	
</script>

<style>
	nav{
		background-color: #22242f;
		height: 65px;
		display: flex;
		justify-content: center;
	}
	.brand {
		height: 50px;
	}
	.linkContainer{
		display: flex;
		align-items: center;
		gap: 50px;
	}

	.linkContainer .navItem {
		color: white;
		font-size: 21px;
		cursor: pointer;
		border-bottom: 2px solid #22242f;
	}

	.linkContainer .navItem:hover{
		color: #fdbe83;
		transition: color 100ms linear;
	}

	.selected{
		border-bottom: 3px solid #FA9C43 !important;
		transform: scale(0.97);
    	transition: border-width .1s
	}

	.selected div {
		color: #FA9C43 !important;
	}

	.selected svg {
		color: #FA9C43 !important;
	}

	a{
		text-decoration: none;
		height: 100%;
	}

	.burger {
		display:none;
		margin: 0;
		padding: 0;
		width: 40px;
		height: 40px;
	}

	.burger img {
		width: 100%;
	}

	.navContainer{
		display: flex;
		justify-content: space-between;
		align-items: center;
		min-width: 1000px;
	}

	.guides{
		color: white;
		font-size: 21px;
		cursor: pointer;
		border-bottom: 2px solid #22242f;
	}

	.guides:hover{
		color: #fdbe83;
		transition: color 100ms linear;
	}

	@media(max-width:1200px){
		.navContainer{
			min-width: 83%;
		}
	}

	@media(max-width:1050px){
		.linkContainer{
			gap: 30px;
		}
	}

	@media(max-width:940px){
		.linkContainer{
			display: none;
		}
		.burger {
			display: block;
		}
	}

	nav {
		box-shadow: 0 4px 4px 0 rgba(0,0,0,.2);
	}

	.navItem{
		padding-top: 4px;
	}
</style>

<nav>
	<div class="navContainer">
	   <div>
		  <a href="."><img class="brand" src="brand.svg" alt="brand logo"></a>
	   </div>
	   <div class="burger">
		<img src="menu.svg" alt="">
	   </div>
	   <div class="linkContainer">
		  <a rel="external" href="team-comps/" class:selected={segment === 'team-comps'}>
		  	<div class="navItem"> Team Comps </div>
		  </a>
		  <a rel="external" href="augments/" class:selected={segment === 'augments'}>
		  	<div class="navItem"> Augments </div>
		  </a>
		  <a rel="external" href="champions/" class:selected={segment === 'champions'}>
		  	<div class="navItem">Champions </div>
		  </a>
		  <a rel="external" href="guides" class="guides navItem" class:selected={segment === 'guides'} style="display: flex; justify-content: center; align-items: center;">
			<div>Guides </div>
			 <svg stroke="currentColor" fill="currentColor" stroke-width="0" viewBox="0 0 24 24" height="35px" width="35px" xmlns="http://www.w3.org/2000/svg">
				<path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
			 </svg>
		  </a>
	   </div>
	</div>
 </nav>