<script>
	import { T } from '@threlte/core';
	import { spring } from 'svelte/motion';
	import * as Three from 'three';
	import { interactivity, OrbitControls } from '@threlte/extras';
	interactivity();
	const scale = spring(1);
</script>

<T.PerspectiveCamera
	makeDefault
	position={[6, 6, 6]}
	on:create={({ ref }) => {
		ref.lookAt(0, 1, 0);
	}}
>
	<OrbitControls enableDamping autoRotate />
</T.PerspectiveCamera>

<T.AmbientLight intensity={1} />
<T.DirectionalLight color="red" intensity={1} position={[-1, 3, -1]} castShadow />

<T.Mesh
	position.y={$scale}
	scale={$scale}
	on:click={() => scale.set($scale === 1 ? 2 : 1)}
	castShadow
>
	<T.BoxGeometry args={[1, 2, 1]} />
	<T.MeshStandardMaterial color="#C27BFF" />
</T.Mesh>

<T.Mesh rotation.x={-Math.PI / 2} receiveShadow>
	<T.CircleGeometry args={[4, 40]} />
	<T.MeshStandardMaterial color="#C27BFF" side={Three.DoubleSide} />
</T.Mesh>
