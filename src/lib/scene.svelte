<script>
	import { T } from '@threlte/core';
	import { OrbitControls, interactivity } from '@threlte/extras';
	interactivity();

	import Ant from './ant.svelte';
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
<T.DirectionalLight color="red" intensity={1} position={[-1, 3, -1]} castShadow />
