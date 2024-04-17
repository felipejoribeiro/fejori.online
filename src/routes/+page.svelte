<script>
	import './global.css';
	import Footer from '$lib/footer.svelte';
	import Scene from '$lib/scene.svelte';
	import { Canvas } from '@threlte/core';
</script>

<svelte:head>
	<title>Felipe J. O. Ribeiro</title>
	<meta name="description" content="Felipe J. O. Ribeiro's personal website" />
</svelte:head>

<main>
	<Canvas>
		<Scene />
	</Canvas>
</main>

<Footer />

<style>
	main {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background: rgb(54, 43, 62);
		background: radial-gradient(circle, rgba(54, 43, 62, 1) 0%, rgba(0, 0, 0, 1) 100%);
		color: white;
	}
</style>
