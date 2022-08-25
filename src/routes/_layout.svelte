<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	.fixed-top {
  		position: fixed;
		top: 0;
		right: 0;
		width: 100%;
		z-index:10
	}
</style>

<div class="fixed-top">
	<Nav {segment}/>
</div>

<main>
	<slot></slot>
</main>