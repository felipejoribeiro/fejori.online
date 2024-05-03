<script lang="ts">
	import { T } from '@threlte/core';
	import { OrbitControls, interactivity } from '@threlte/extras';
	interactivity();

	import Ant from './ant.svelte';

	let light: {
		intensity: number;
		position: [number, number, number];
	} = {
		intensity: 29,
		position: [0, 2, 0]
	};

	let sphere: {
		position: [number, number, number];
	} = {
		position: [0, 2, 0]
	};

	function float() {
		const timeInSeconds = Date.now() / 1000;
		const offset = 2.9;
		light.position = [Math.sin(timeInSeconds) * offset, 2, Math.cos(timeInSeconds) * offset];
		sphere.position = [Math.sin(timeInSeconds) * offset, 2, Math.cos(timeInSeconds) * offset];
		requestAnimationFrame(float);
	}

	float();
</script>

<T.PerspectiveCamera
	makeDefault
	position={[5, 5, 5]}
	on:create={({ ref }) => {
		ref.lookAt(0, 3, 0);
	}}
>
	<OrbitControls enableDamping autoRotate />
</T.PerspectiveCamera>

<Ant scale={4} position.y={-3} />

<T.AmbientLight intensity={1} />
<T.PointLight {...light} />

<T.DirectionalLight color="red" intensity={1} position={[-1, 3, -1]} castShadow />

<T.Mesh position={sphere.position}>
	<T.SphereGeometry args={[0.05, 8, 8]} />
	<T.MeshStandardMaterial color="white" emissiveIntensity={20} emissive="white" />
</T.Mesh>
