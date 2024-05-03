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
	<div class="canvas-container">
		<Canvas>
			<Scene />
		</Canvas>
	</div>
</main>

<Footer />

<style>
	main {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
		background: rgb(54, 43, 62);
		background: radial-gradient(circle, rgba(54, 43, 62, 1) 0%, rgba(0, 0, 0, 1) 100%);
		color: white;
	}

	.canvas-container {
		width: 100%;
		height: 80vh;
		display: flex;
		justify-content: flex-start;
		overflow: visible;
	}
</style>
